<template>
  <div :class="vp && 'vpInfo'" class="titulo">
    <div class="tituloInfo">
      <h2>
        {{ filme }}
      </h2>
    </div>
  </div>
</template>

<script>
export default {
  name: "TituloComponent",
  props: {
    filme: String,
    vp: Boolean,
  },
};
</script>
<style scoped>
.titulo {
  width: 25vw;
  padding-left: 20px;
  display: flex;
  align-items: center;
  color: #ffffff;
  background-color: #222121;
}
.tituloInfo {
  text-align: left;
}
.vpInfo {
  color: #b8a996;
  background: linear-gradient(
    90deg,
    rgba(49, 45, 35, 1) 50%,
    rgba(29, 25, 19, 1) 100%
  );
}
</style>
