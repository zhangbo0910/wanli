<template>
  <div class="box">
    <a-layout>
      <a-layout-sider class="nav_box" :trigger="null">
          <div class="nav_logo"><img src="../../assets/img/logo_nav.png" alt=""></div>
        <Sidebar></Sidebar> 
      </a-layout-sider>
      <a-layout>
        <a-layout-header class="hends">
          <Hends></Hends>
        </a-layout-header>
        <a-layout-content class="padding_">
          <router-view>
          </router-view>
        </a-layout-content>
      </a-layout>
    </a-layout>
      <a-layout-footer class="foot_">Footer</a-layout-footer>
  </div>
</template>

<script>
import Sidebar from "../sidebar/sidebar.vue";
import Hends from "../hender/hender.vue";
export default {
  data() {
    return {};
  },
  methods: {},
  components: {
    Sidebar,Hends
  }
};
</script>

<style scoped>
.box {
  height: 100%;
}
.ant-layout {
  height: 100%;
}
.nav_box {
  height: 100%;
  width: 300px !important;
  min-width: 300px !important;
  background: #001529;
}
.foot_{
    width: 100%;
    height: 40px;
    background: #cccccc;
    position: fixed;
    bottom: 0;
    z-index: 100;
}
.nav_logo>img{
    height:64px;
    width:300px;
}
.padding_{
  padding: 20px 40px;
}
.hends{
  background: #ffffff;
  border:1px solid #bbbbbb;
  text-align: end;
}
</style>
