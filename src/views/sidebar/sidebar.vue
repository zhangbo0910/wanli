<template>
  <div>
    <a-menu
      mode="inline"
      :openKeys="openKeys"
      @openChange="onOpenChange"
      style="width: 300px"
      theme="dark"
    >
      <a-sub-menu key="sub1">
        <span slot="title">
          <router-link to="/home">
            <a-icon type="home" />
            <span>主页</span>
          </router-link>
        </span>
      </a-sub-menu>

      <a-sub-menu key="sub2">
        <span slot="title">
          <a-icon type="car" />
          <span>车辆管理</span>
        </span>
        <a-menu-item key="1">
          <router-link to="/shishijiankong">实时监控</router-link>
        </a-menu-item>
        <a-menu-item key="2">
          <router-link to="/xianluguanli">线路管理</router-link>
        </a-menu-item>
        <a-menu-item key="a">
          <router-link to="/zhaopianguanli">照片管理</router-link>
        </a-menu-item>
        <a-menu-item key="b">
          <router-link to="/diaoduchaxun">调度查询</router-link>
        </a-menu-item>
        <!-- <a-sub-menu key="sub3" title="Submenu">
          <a-menu-item key="3">Option 7</a-menu-item>
          <a-menu-item key="4">Option 8</a-menu-item>
        </a-sub-menu>-->
      </a-sub-menu>

      <a-sub-menu key="sub3">
        <span slot="title">
          <a-icon type="setting" />
          <span>统计查询</span>
        </span>
        <a-menu-item key="5">
          <router-link to="/chaosutongji">超速统计</router-link>
        </a-menu-item>
        <a-menu-item key="6">
          <router-link to="/pilao">疲劳驾驶统计</router-link>
        </a-menu-item>
        <a-menu-item key="7">
          <router-link to="/shangxian">车辆上线率统计</router-link>
        </a-menu-item>
        <a-menu-item key="8">
          <router-link to="/yichang">车辆异常统计</router-link>
        </a-menu-item>
        <a-menu-item key="c">
          <router-link to="/az_weishangxian">车辆安装未上线统计</router-link>
        </a-menu-item>
        <a-menu-item key="d">
          <router-link to="/jr_weishangxian">车辆近几天未上线统计</router-link>
        </a-menu-item>
        <a-menu-item key="e">
          <router-link to="/guijiwanzheng">轨迹完整率</router-link>
        </a-menu-item>
        <a-menu-item key="f">
          <router-link to="/shujvhege">数据合格率</router-link>
        </a-menu-item>
      </a-sub-menu>

      <a-sub-menu key="sub4">
        <span slot="title">
          <a-icon type="setting" />
          <span>安全管理</span>
        </span>
        <a-menu-item key="9">
          <router-link to="/gaojing">告警处理</router-link>
        </a-menu-item>
        <a-menu-item key="10">
          <router-link to="/xiansu">限速处理</router-link>
        </a-menu-item>
      </a-sub-menu>

      <a-sub-menu key="sub5">
        <span slot="title">
          <a-icon type="setting" />
          <span>证据查询</span>
        </span>
        <a-menu-item key="13">Option 9</a-menu-item>
      </a-sub-menu>

      <a-sub-menu key="sub6">
        <span slot="title">
          <a-icon type="setting" />
          <span>规则管理</span>
        </span>
        <a-menu-item key="17"><router-link to="/weihu">规则维护</router-link></a-menu-item>
        <a-menu-item key="18"><router-link to="/fenpei">规则分配</router-link></a-menu-item>
        <a-menu-item key="19"><router-link to="/shengji">自动升级</router-link></a-menu-item>
      </a-sub-menu>
    </a-menu>
  </div>
</template>

<script>
export default {
  data() {
    return {
      rootSubmenuKeys: ["sub1", "sub2", "sub3", "sub4", "sub5", "sub6"],
      openKeys: ["sub1"] // ,  默认打开的下拉菜单
    };
  },
  methods: {
    onOpenChange(openKeys) {
      console.log(openKeys);
      const latestOpenKey = openKeys.find(
        key => this.openKeys.indexOf(key) === -1
      );
      if (this.rootSubmenuKeys.indexOf(latestOpenKey) === -1) {
        this.openKeys = openKeys;
      } else {
        this.openKeys = latestOpenKey ? [latestOpenKey] : [];
      }
    }
  },
  components: {}
};
</script>

<style scoped>
/* .nav_btn{
    height: 50px;
    
}
.nav_btn span{
    font-size:20px;
} */
.ant-menu-submenu,
.ant-menu-item {
  /* border-top:1px solid #ccc; */
  /* border-bottom:1px solid #ccc;  */
}
</style>
