<template>
  <div class="exibicao">
    <div v-if="vp" class="vpInfo">PREMIER</div>
    <div v-else>
      <div v-if="xd" class="exibicaoXd">
        <h2>XD</h2>
        <p class="dboxInfo" v-if="dbox">DBOX</p>
      </div>
      <div v-if="no" class="exibicaoNo">
        <h2>2D</h2>
        <p class="dboxInfo" v-if="dbox">DBOX</p>
      </div>
      <div v-if="tresd" class="exibicaoTresd">
        <h2>3D</h2>
        <p class="dboxInfo" v-if="dbox">DBOX</p>
      </div>
      <div v-if="xtres">
        <div class="exibicaoXtres">
          <h2 class="exibicaoTresd">3D</h2>
          <h2 class="exibicaoXdd">XD</h2>
        </div>
        <h2 class="dboxInfo" v-if="dbox">DBOX</h2>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ExibicaoComponent",
  props: {
    xd: Boolean,
    no: Boolean,
    tresd: Boolean,
    xtres: Boolean,
    dbox: Boolean,
    vp: Boolean,
  },
};
</script>
<style scoped>
.exibicao {
  width: 110px;
  padding: 15px 0px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(
    90deg,
    rgba(76, 77, 74, 1) 50%,
    rgba(101, 101, 96, 1) 100%
  );
}
.exibicaoXd {
  padding: 6px 0px;
  color: white;
  text-shadow: 0 0 7px #b3aeae, 0 0 10px #b3aeae, 0 0 21px #b3aeae,
    0 0 42px #b3aeae, 0 0 82px #b3aeae, 0 0 92px #b3aeae, 0 0 102px #b3aeae,
    0 0 151px #b3aeae;
}
.exibicaoXd h2 {
  -webkit-text-stroke: 0.4px rgb(231, 97, 49);
}
.exibicaoXdd {
  padding: 6px 0px;
  color: white;
  text-shadow: 0 0 7px #b3aeae, 0 0 10px #b3aeae, 0 0 21px #b3aeae,
    0 0 42px #b3aeae, 0 0 82px #b3aeae, 0 0 92px #b3aeae, 0 0 102px #b3aeae,
    0 0 151px #b3aeae;
  -webkit-text-stroke: 0.4px rgb(231, 97, 49);
}
.exibicaoNo {
  padding: 6px 0px;
  color: gray;
  text-shadow: 0px 3px 2px rgba(0, 0, 0, 0.4);
}
.exibicaoTresd {
  padding: 6px 0px;
  color: white;
  text-shadow: 0 0 7px #fff, 0 0 10px #fff, 0 0 21px #fff, 0 0 42px #fff,
    0 0 82px #fff, 0 0 92px #fff, 0 0 102px #fff, 0 0 151px #fff;
}
.exibicaoXtres {
  display: flex;
  gap: 5px;
}
.dboxInfo {
  font-size: 10px;
  box-shadow: unset;
  border: unset;
  color: #eaa311;
  text-shadow: 0 0 7px #eaa311, 0 0 10px #eaa311, 0 0 21px #eaa311,
    0 0 42px #eaa311, 0 0 82px #eaa311, 0 0 92px #eaa311, 0 0 102px #eaa311,
    0 0 151px #eaa311;
}
.vpInfo {
  font-size: 14px;
  font-weight: 700;
  box-shadow: unset;
  border: unset;
  color: #e8dc95;
  text-shadow: 0 0 7px #e8dc95, 0 0 10px #e8dc95, 0 0 21px #e8dc95,
    0 0 42px #e8dc95, 0 0 82px #e8dc95, 0 0 92px #e8dc95, 0 0 102px #e8dc95,
    0 0 151px #e8dc95;
}
</style>
