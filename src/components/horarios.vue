<template>
  <div
    :class="[
      !out && vp ? 'vpInfo' : '',
      !out ? '' : 'outFilme',
      // isStarting(time),
    ]"
    class="filmeInfo"
  >
    <div class="horario">
      <h2>{{ time.replace("h", ":") }}</h2>
    </div>
    <div v-if="out" class="esgotado">ESGOTADA</div>
    <div v-else class="horarioInfo">
      <p v-if="leg">LEG</p>
      <p v-if="dub">DUB</p>
      <p v-if="ori">ORI</p>
      <p v-if="sem">SEM</p>
      <h6 v-if="dbox" class="dboxInfo">D-BOX</h6>
    </div>
  </div>
</template>

<script>
export default {
  name: "HorariosComponent",
  props: {
    time: String,
    leg: Boolean,
    dub: Boolean,
    ori: Boolean,
    sem: Boolean,
    dbox: Boolean,
    out: Boolean,
    vp: Boolean,
  },

  methods: {
    isStarting(time) {
      const sessionTime = new Date(Date.now());
      const [hour, minute] = time.split("h");
      sessionTime.setHours(parseInt(hour, 10));
      sessionTime.setMinutes(parseInt(minute, 10));
      const diff = (sessionTime.getTime() - Date.now()) / 1000 / 60;
      console.log(diff);
      return diff < 15 && diff > 0 ? "starting" : "";
    },
  },
};
</script>
<style scoped>
.filmeInfo {
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: center;
  padding: 5px 0px;
  flex-direction: column;
  align-items: center;
  color: #202123;
  border-right: 0.5px solid #585c60;
  border-bottom: 0.5px solid #585c60;
  background: linear-gradient(
    180deg,
    rgba(152, 155, 156, 1) 0%,
    rgba(140, 142, 144, 1) 50%
  );
}
.outFilme {
  background: linear-gradient(
    180deg,
    rgba(236, 59, 28, 1) 0%,
    rgba(186, 37, 21, 1) 50%
  );
}
.horario {
  text-align: center;
  width: 100%;
}
.horario h2 {
  font-size: 32px;
}
.esgotado {
  font-size: 16px;
  font-weight: 700;
  color: #202123;
}
.horarioInfo {
  display: flex;
  text-align: center;
  justify-content: center;
  width: 100%;
  color: #202123;
}
.horarioInfo p {
  width: 30%;
  padding: 4px 4px 0.5px 4px;
  font-size: 12px;
  font-weight: 700;
  box-shadow: inset 0px 3px 2px rgba(0, 0, 0, 0.2);
  background-color: transparent;
  border-radius: 8px;
  background: linear-gradient(
    180deg,
    rgba(152, 155, 156, 1) 0%,
    rgba(140, 142, 144, 1) 50%
  );
}
.dboxInfo {
  padding-top: 4px;
  padding-left: 5px;
  box-shadow: unset !important;
  border: unset !important;
  color: rgb(255, 174, 0);
  text-shadow: 0px 3px 2px rgba(0, 0, 0, 0.2);
}
.vpInfo {
  color: #b8a996;
  background: linear-gradient(
    90deg,
    rgba(49, 45, 35, 1) 50%,
    rgba(29, 25, 19, 1) 100%
  );
}
.starting {
  color: #202123;
  background: linear-gradient(
    180deg,
    rgb(63, 236, 28) 0%,
    rgb(40, 186, 21) 50%
  );
}
</style>
