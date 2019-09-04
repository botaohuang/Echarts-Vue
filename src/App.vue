<template>
  <div id="app">
    <div style="height:140px; width:400px;">
      <huanzhuang :ecData="ecData" :totalNum="totalNum"></huanzhuang>
    </div>
  </div>
</template>

<script>
import huanzhuang from "./components/chart/huanzhuang.vue";
import { setInterval } from 'timers';

export default {
  name: "app",
  components: {
    huanzhuang
  },
  data() {
    return {
      ecData: [
        { name: "未执行",percent: "0.00%", num:"12" },
        { name: "执行中",percent: "0.00%", num:"17" },
        { name: "执行成功",percent: "97.67%", num:"22" },
        { name: "执行失败",percent: "2.33%", num:"27" }
      ],
      totalNum:78
    };
  },

  mounted() {
    setInterval(()=>{
      this.ecData= [
        { name: "未执行",percent: "0.00%", num:Math.ceil(Math.random()*100) },
        { name: "执行中",percent: "0.00%", num:Math.ceil(Math.random()*100) },
        { name: "执行成功",percent: "97.67%", num:Math.ceil(Math.random()*100) },
        { name: "执行失败",percent: "2.33%", num:Math.ceil(Math.random()*100) }
      ],
      this.totalNum= Math.ceil(Math.random()*100)
    },3000)
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
