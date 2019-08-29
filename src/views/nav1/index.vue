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
          <div class="item_p">{{zaixian}}</div>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="6">
        <div class="gutter-box">
          <p class="tit_p">车辆分布信息图</p>
          <div class="item_p">{{lixian}}</div>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="4">
        <div class="gutter-box">
          <p class="tit_p">企业公告</p>
          <div class="item_p">{{ruwang}}</div>
        </div>
      </a-col>
    </a-row>

    <a-row :gutter="{ xs: 8, sm: 16, md: 24, lg: 32 }" class="margin_row">
      <a-col class="gutter-row" :span="12">
        <div class="gutter-box">
          <p class="tit_p">车辆报警情况</p>
          <div class="item_p">{{zaixian}}</div>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="6">
        <div class="gutter-box">
          <p class="tit_p">报警统计</p>
          <div class="item_p">{{lixian}}</div>
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
      ruwang:"0 0 0 3 3"
    }
  },
  methods: {

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
</style>
