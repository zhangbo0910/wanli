<template>
  <div>
      <div class="user_box">
        <div class="gutter-box" v-for="(item,index) in titdata" :key="index">
          <a-icon type="user" />
          <p><a-button>{{item}}</a-button></p>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titdata:["疲劳规则","禁入规则","禁出规则","区域限速","线路偏移","分段限速","关键点","停车超时","行车规则","定时拍照","定时录像","道路超速","报警联动","异常定位","二级警报"]
    }
  },
  methods: {

  },
  components: {

  }
}
</script>

<style scoped>
.gutter-box{
  text-align: center;
  flex: 1;
  border-bottom:3px solid #bbb; 
}
.ant-btn {
  padding: 0 5px;
}
.anticon-user{
  font-size: 40px;
}
.user_box{
  display: flex;
}
</style>
