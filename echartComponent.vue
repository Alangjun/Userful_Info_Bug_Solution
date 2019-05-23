<template>
  <div :id="id" class="echarts-element-class"></div>
</template>

<script>
  import echarts from 'echarts/lib/echarts';
  import 'echarts/lib/chart/line'
  import 'echarts/lib/chart/pie'
  import 'echarts/lib/component/tooltip'
  import 'echarts/lib/component/legend'
  import 'echarts/lib/component/title'
  export default {
    components:{echarts},
    props: {
      options: {  //父组件传递的options
        type: Object,
        default: {}
      },
      id: {  //echarts元素的id
        type: String,
        default: 'id'
      }
    },
    data(){
     return{}
    },
    watch:{
      options(){ //监听父组件传来的option是否有变化
        this.optionChanged(this.options)
      }
    },
    methods:{
      resizeHander(){
        this.initEcharts(this.id).resize()
      },
      optionChanged(option){
        this.echartsSetOption(this.id, option);
        window.addEventListener('resize',this.resizeHander)  //监听echarts图标resize事件
      },
      echartsSetOption(echart_ele_id,echart_ele_option){
        let temp = echarts.init(document.getElementById(echart_ele_id)) ;
        temp.setOption(echart_ele_option)
      },
      initEcharts(echart_ele_id){
        return echarts.init(document.getElementById(echart_ele_id))
      }
    },
    beforeDestroy(){ // 注意这里不能使用destoryed 否则无法移除window的resize事件
      window.removeEventListener("resize",this.resizeHander)
    }
  }
</script>

<style lang="scss">
.echarts-element-class{
  width: 100%;
  height: 250px;
  background-color: #fff;
}
</style>
