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
      <a-col span="6" class="bag"> 123124324324523</a-col>
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
          }]

    };
  },
  methods: {
      getMap() {
          // amap vue component
          console.log(amapManager._componentMap);
          // gaode map instance
          console.log(amapManager._map);
        }

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
    .bag{
      background: #000;
    }
</style>
