<template>
  <div>
    <a-row>
      <a-col :span="24" class="border">
        <router-link to="/xianluguanli"><a-button type="primary">线路管理</a-button></router-link>
        <router-link to="/bangdingluxian"><a-button>车辆绑定路线查询</a-button></router-link>
      </a-col>
    </a-row>
      <router-view></router-view>
  </div>
</template>

<script>

export default {
  data() {
    return {
     switch:true
    };
  },
  methods: {
  
  },
  components: {}
};
</script>

<style scoped>
.border {
  border-bottom: 4px solid #bebebe;
  padding-left: 60px;
}
.border .ant-btn {
  height: 40px;
}

</style>
