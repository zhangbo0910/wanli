<template>
  <div>
    <a-row :gutter="{ xs: 8, sm: 16, md: 24, lg: 32 }">
      <a-col class="gutter-row" :span="6">
        <div class="gutter-box">
          <p class="tit_p">在线车辆数</p>
          <div class="item_p">{{zaixian}}</div>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="6">
        <div class="gutter-box">
          <p class="tit_p">离线车辆数</p>
          <div class="item_p">{{lixian}}</div>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="6">
        <div class="gutter-box">
          <p class="tit_p">入网车辆数</p>
          <div class="item_p">{{ruwang}}</div>
        </div>
      </a-col>
    </a-row>

    <a-row :gutter="{ xs: 8, sm: 16, md: 24, lg: 32 }" class="margin_row">
      <a-col class="gutter-row" :span="8">
        <div class="gutter-box">
          <p class="tit_p">车辆综合信息</p>
          <div id="pie" :style="{ height: '270px'}"></div>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="6">
        <div class="gutter-box">
          <p class="tit_p">车辆分布信息图</p>
            <div :style="{ height: '270px'}"></div>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="4">
        <div class="gutter-box">
          <p class="tit_p">企业公告</p>
          <div :style="{ height:'270px', padding:'20px'}" @click="location">欢迎使用中中北斗星定位服务！</div>
        </div>
      </a-col>
    </a-row>

    <a-row :gutter="{ xs: 8, sm: 16, md: 24, lg: 32 }" class="margin_row">
      <a-col class="gutter-row" :span="12">
        <div class="gutter-box">
          <p class="tit_p">车辆报警情况</p>
          <div id="bargraph" :style="{width:'620px',height:'300px'}">
          </div>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="6">
        <div class="gutter-box">
          <p class="tit_p">报警统计</p>
          <div class="item_p">
            <table class="bor_" border="1" :style="{width:'100%'}">
                <tr v-for="(item,index) in tableData" :key="index" class="row_" >
                    <td :style="{background:'#c6ddea'}">{{item.data}}</td>
                    <td>{{item.items}}</td>
                </tr>
            </table>
          </div>
        </div>
      </a-col>
    </a-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      zaixian:"0 0 0 1 2",
      lixian:"0 0 0 2 1",
      ruwang:"0 0 0 3 3",
       tableData:[
            {
                data:"车辆报警总数",
                items:"6146"
            },{
                data:"超速报警",
                items:"0"
            },{
                data:"紧急报警",
                items:"0"
            },{
                data:"疲劳报警",
                items:"2034"
            }
        ]
    }
  },
  mounted(){
    this.pie();
    this.bargraph();
  },
  methods: {
    pie(){//在线离线车辆饼图
           // 基于准备好的dom，初始化echarts实例
        let myChart = this.$echarts.init(document.getElementById('pie'));
        // 绘制图表
         myChart.setOption({
    title : {
        x:'center'
    },
    tooltip : {
        trigger: 'item',
        formatter: "{a} <br/>{b} : {c} ({d}%)"
    },
    legend: {
        orient: 'vertical',
        left: 'left',
        // data: ['离线车辆','在线车辆']
    },
    series : [
        {
            name: '车辆综合信息',
            type: 'pie',
            radius : '55%',
            center: ['50%', '60%'],
            data:[
                {value:335, name:'离线车辆'},
                {value:1548, name:'在线车辆'}
            ],
            itemStyle: {
                emphasis: {
                    shadowBlur: 10,
                    shadowOffsetX: 0,
                    shadowColor: 'rgba(0, 0, 0, 0.5)'
                }
            }
        }
    ]
});
    },

    //
    location(){
    alert('欢迎使用中中北斗星定位服务！')
    },
 bargraph(){
         let Chart = this.$echarts.init(document.getElementById('bargraph'));
         Chart.setOption( {
    xAxis: {
        type: 'category',
        data: ['禹州公司', '豪华汽车站', '客运四公司']
    },
    yAxis: {
        type: 'value'
    },
    series: [{
        data: [200, 100, 100],
        type: 'bar'
    }]
})
    }

  },
  components: {

  }
}
</script>

<style scoped>
.ant-row > div {
  background: transparent;
  border: 0;
  }
.gutter-box {
  /* padding: 5px 0; */
  border:1px solid #bbbbbb;
}
.tit_p{
  text-align: center;
  background: #95a0a6;
  color: #ffffff;
  line-height: 30px;
  margin: 0;
}
.item_p{
  text-align: center;
  line-height: 50px;
}
.margin_row{
  margin-top:15px;
}
.row_ td{
  width:50%;
  line-height: 74px;
}
.bor_{
  border-top:none; 
 border-color: #bbbbbb;
}
</style>
