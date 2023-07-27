<template>
  <div>
    <div v-for="(item, x) in filmesAgrupados" :key="x">
      <div class="column">
        <Titulo :filme="item.nomeFilme" :vp="item.stringPoltrona === 'VP'" />
        <Idades
          :livre="item.idadeMinima === '0 '"
          :dez="item.idadeMinima === '10'"
          :doze="item.idadeMinima === '12'"
          :quatorze="item.idadeMinima === '14'"
          :dezesseis="item.idadeMinima === '16'"
          :dezoito="item.idadeMinima === '18'"
        />
        <Exibicao
          :xd="item.tipoExibicao === 'XD'"
          :no="item.tipoExibicao === 'NO'"
          :tresd="item.tipoExibicao === '3D'"
          :xtres="item.tipoExibicao === 'X3'"
          :dbox="item.stringPoltrona === 'DB'"
          :vp="item.stringPoltrona === 'VP'"
        />
        <div class="horaiosDiv">
          <div v-for="hora in item.horaSessao" :key="hora" class="horarioInfo">
            <Horarios
              :time="hora"
              :out="item.sessao === 'S'"
              :leg="item.siglaLegenda === 'L'"
              :dub="item.siglaLegenda === 'D'"
              :ori="item.siglaLegenda === 'V'"
              :sem="item.siglaLegenda === 'S'"
              :dbox="item.stringPoltrona === 'DB'"
              :vp="item.stringPoltrona === 'VP'"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import txt from "raw-loader!../assets/GRADE_DESTAQUE_688.txt";
import moment from "moment";
import Horarios from "./horarios.vue";
import Idades from "./idade.vue";
import Exibicao from "./exibicao.vue";
import Titulo from "./titulo.vue";

export default {
  components: { Horarios, Idades, Exibicao, Titulo },
  name: "CatalogoComponent",

  methods: {
    loadRooms() {
      const grade = txt.split("\n");

      if (grade.length === 0) {
        return [];
      }

      const result = grade.reduce((arrays, coluna) => {
        const [
          horaSessao,
          nomeFilme,
          idadeMinima,
          siglaLegenda,
          sessao,
          tipoExibicao,
          stringPoltrona,
        ] = [
          coluna.substring(10, 15),
          coluna.substring(15, 75),
          coluna.substring(75, 77),
          coluna.substring(80, 81),
          coluna.substring(81, 82),
          coluna.substring(91, 93),
          coluna.substring(174, 176),
        ];

        const complete =
          nomeFilme &&
          idadeMinima &&
          tipoExibicao &&
          horaSessao &&
          siglaLegenda &&
          sessao &&
          stringPoltrona;

        arrays.push({
          horaSessao,
          nomeFilme,
          idadeMinima,
          siglaLegenda,
          sessao,
          tipoExibicao,
          stringPoltrona,
          complete,
        });

        return arrays;
      }, []);

      this.rooms = result.filter((item) => item.complete);
    },
  },

  computed: {
    filmesAgrupados() {
      const filmesAgrupados = {};

      this.rooms.forEach((room) => {
        const chave = room.nomeFilme + room.tipoExibicao;

        if (filmesAgrupados[chave]) {
          filmesAgrupados[chave].horaSessao.push(room.horaSessao);
        } else {
          filmesAgrupados[chave] = {
            horaSessao: [room.horaSessao],
            nomeFilme: room.nomeFilme,
            idadeMinima: room.idadeMinima,
            siglaLegenda: room.siglaLegenda,
            sessao: room.sessao,
            tipoExibicao: room.tipoExibicao,
            stringPoltrona: room.stringPoltrona,
            complete: room.complete,
            segundosFaltando: "NÃO",
          };
        }
      });

      const resultado = Object.values(filmesAgrupados).sort((a, b) => {
        if (a.nomeFilme === b.nomeFilme && a.tipoExibicao === b.tipoExibicao) {
          return a.horaSessao[0].localeCompare(b.horaSessao[0]);
        }
        return 0;
      });

      return resultado;
    },
  },

  created() {
    this.loadRooms();
    setInterval(() => {
      this.filmesAgrupados.forEach((r) => {
        const data_sala = moment(r.horaSessao);
        const data_agora = moment();
        const result = data_sala.diff(data_agora, "seconds");
        r.horaSessao = result;
      });
    }, 5000);
  },
};
</script>

<style scoped>
.column {
  display: flex;
  width: fit-content;
  min-width: 100%;
  border: 0.5px solid #585c60;
  background: linear-gradient(
    180deg,
    rgba(152, 155, 156, 1) 0%,
    rgba(140, 142, 144, 1) 50%
  );
}
.horaiosDiv {
  display: inline-grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  flex: 1;
}
.horarioInfo {
  display: inline-block;
}
</style>
