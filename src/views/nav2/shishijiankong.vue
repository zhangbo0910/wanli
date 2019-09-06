<template>
  <div class="map_box">
    <a-row>
      <a-col :span="24" class="tit_">实时告警</a-col>
    </a-row>
    <a-row>
      <a-col span="18">
        <div class="amap-page-container">
      <el-amap ref="map" vid="amapDemo" :amap-manager="amapManager" :center="center" :zoom="zoom" :plugin="plugin" :events="events" class="amap-demo">
      </el-amap>
    </div>
      </a-col>
      <a-col span="6" class="pad" style="background:#c6ddea;">
        <div class="tab_box">
              <a-button>车辆</a-button>
              <a-button>关注</a-button>
        </div>
        <div class="search_">
        <select  style="width:28%;height:32px;border-radius:4px;">
            <option>车牌号</option>
            <option>卡号</option>
        </select>
         <a-input placeholder="单行输入" style="margin:0 5px;width:50%;"/>
          <a-button>查询</a-button>
        </div>
          <div class="search_">
            <a-button class="btn_" v-for="(item,index) in btnarr" :key="index">{{item}}</a-button>
          </div>
      </a-col>
    </a-row>
  </div>
</template>

<script>
//  import { AMapManager } from 'vue-amap';
import VueAMap from 'vue-amap';
 let amapManager = new VueAMap.AMapManager();
export default {
  data() {
    return {
      btnarr:["全部","行驶","停止","离线","刷新"],
      currency:'',
      amapManager,
          zoom: 12,
          center: [113.6249300000,34.7472500000],
          events: {
            init: (o) => {
              // o 是高德地图定位插件实例
              console.log(o.getCenter()),
              console.log(this.$refs.map.$$getInstance()),
              o.getCity(result => {
                console.log(result)
              })
            },
            'moveend': () => {
            },
            'zoomchange': () => {
            },
            'click': (e) => {
              alert('map clicked');
            }
          },
          plugin: ['ToolBar', {
            pName: 'MapType',
            defaultType: 0,
            events: {
              init(o) {
                console.log(o);
              }
            }
          },
          {
            pName: 'OverView',
            events: {
              init(instance) {
                console.log(instance);
              }
            }
          }]

    };
  },
  methods: {
      getMap() {
          // amap vue component
          console.log(amapManager._componentMap);
          // gaode map instance
          console.log(amapManager._map);
        },
        handleCurrencyChange (currency) {
          console.log(currency);
        },

  },
  components: {}
};
</script>

<style scoped>
.amap-wrapper {
  width: 100%;
  height: 600px;
}
.map_box {
  margin-left: -39px;
}
.tit_{
  height: 40px;
  background-color: rgb(198, 221, 234);
  line-height: 40px;
  margin-top: -20px;
  border-bottom:1px solid #42a8ec; 
  text-indent: 30px;
}
.amap-demo {
      height:788px;
    }
.pad{
      padding: 20px 30px;
}
.tab_box{
  height:120px;
  background: #95a0a6;
  border-radius:10px;
  text-align: center;
}
.tab_box button{
  width:85px;
  height:45px;
  margin-top:70px;
  font-size: 20px;
}
.search_{
  display: flex;
  margin-top: 10px;
}
.btn_{
  width:60px;
  margin-right: 10px;
  padding: 0;
}
.search_ :last-child{
  margin: 0;
}
</style>
