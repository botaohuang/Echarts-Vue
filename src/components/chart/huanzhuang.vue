<template>
  <section ref="instance" style="width:100%;height:100%;"></section>
</template>
<script type="text/javascript">
import echarts from "echarts";
export default {
  data() {
    return {};
  },
  props:{
    ecData:{
      type: Array,
      default:[]
    },
    totalNum:{
      type: Number,
      default:0
    }
  },
  mounted() {
    this.initOption();
  },
  methods: {
    initOption() {
      let myChart = echarts.init(this.$refs.instance);
      var option = {
        color:['#ccc','#222','#aaa','#ddd'],// 图例颜色
        title: {
          itemGap:0,
          subtext: "实例总数",
          text: this.totalNum,
          x: "center",
          y: "center",
          subtextStyle: {
            color: "#666",
            fontSize: 12,

          },
          textStyle: {
            fontSize: 22,
            fontWeight: "normal",
            color: ["#333"]
          }
        },
        tooltip: {
          trigger: "item",
          formatter: "{a} <br/>{b}: {c} ({d}%)"
        },
        legend: {
          orient: "vertical",
          y: "center",
          right: 1,
          padding: [15, 40],
          data: this.ecData.map((item,index)=>{return item.name})
        },
        series: [
          {
            name: "实例总数"+this.totalNum,
            type: "pie",
            radius: ["50%", "65%"],
            avoidLabelOverlap: false,
            label: {
              normal: {
                show: false,
                position: "center"
              },
              emphasis: {
                show: false,
                textStyle: {
                  fontSize: "30",
                  fontWeight: "bold"
                }
              }
            },
            labelLine: {
              normal: {
                show: true
              }
            },
            data: this.ecData.map((item,index)=>{
              return {value:item.num,name:item.name}
            })
          }
        ]
      };

      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    }
  },
  watch: {
    ecData(newvalue,oldvalue){
      this.initOption();
    },
    totalNum(newvalue,oldvalue){
      this.initOption();
    }
    
  }
};
</script>