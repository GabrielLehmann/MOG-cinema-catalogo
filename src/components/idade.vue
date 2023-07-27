<template>
  <div class="idade">
    <div class="idadeBox">
      <div v-if="livre" class="idadeLivre">
        <h2>L</h2>
      </div>
      <div v-if="dez" class="idadeDez">
        <h2>10</h2>
      </div>
      <div v-if="doze" class="idadeDoze">
        <h2>12</h2>
      </div>
      <div v-if="quatorze" class="idadeQuatorze">
        <h2>14</h2>
      </div>
      <div v-if="dezesseis" class="idadeDezesseis">
        <h2>16</h2>
      </div>
      <div v-if="dezoito" class="idadeDezoito">
        <h2>18</h2>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "IdadesComponent",
  props: {
    idade: String,
    livre: Boolean,
    dez: Boolean,
    doze: Boolean,
    quatorze: Boolean,
    dezesseis: Boolean,
    dezoito: Boolean,
  },
};
</script>
<style scoped>
.idade {
  width: 83px;
  padding: 5px 0px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #292b2f;
}
.idadeLivre {
  padding: 6px 14px;
  border-radius: 4px;
  background: linear-gradient(
    180deg,
    rgb(70, 236, 28) 0%,
    rgb(40, 186, 21) 50%
  );
}
.idadeDez {
  padding: 6px 10px;
  border-radius: 4px;
  background: linear-gradient(
    180deg,
    rgb(28, 236, 225) 0%,
    rgb(21, 175, 186) 50%
  );
}
.idadeDoze {
  padding: 6px 10px;
  border-radius: 4px;
  background: linear-gradient(
    180deg,
    rgb(236, 222, 15) 0%,
    rgb(235, 222, 32) 50%
  );
}
.idadeQuatorze {
  padding: 6px 10px;
  border-radius: 4px;
  background: linear-gradient(
    180deg,
    rgb(236, 129, 28) 0%,
    rgb(186, 101, 21) 50%
  );
}
.idadeDezesseis {
  padding: 6px 10px;
  border-radius: 4px;
  background: linear-gradient(
    180deg,
    rgb(236, 28, 28) 0%,
    rgb(186, 21, 21) 50%
  );
}
.idadeDezoito {
  padding: 6px 10px;
  border-radius: 4px;
  background: linear-gradient(180deg, rgb(29, 31, 28) 0%, rgb(0, 0, 0) 50%);
}
.idadeBox {
  box-shadow: 0px 4px 2px rgba(0, 0, 0, 0.2);
  color: white;
}
</style>
