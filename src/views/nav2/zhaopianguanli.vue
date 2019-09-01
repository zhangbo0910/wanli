<template>
  <div>
<a-row :gutter="15" class="picture">
      <a-col class="gutter-row" :span="5">
        <div class="gutter-box">
          公司名称：
          <select  class="form-control">
             <option>全部</option>
             <option>许昌总公司</option>
             <option>客运一公司</option>
             <option>禹州公司</option>
          </select>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="2">
        <div class="gutter-box">
          <span>车牌号：</span>
        </div>
      </a-col>
    <a-col class="gutter-row" :span="3">
        <div class="gutter-box">
          <a-input placeholder="单行输入"/>
        </div>
      </a-col>

      <a-col class="gutter-row" :span="2">
        <div class="gutter-box">起始时间:</div>
      </a-col>
 <a-col class="gutter-row" :span="5">
        <div class="gutter-box"><a-range-picker @change="onChange" /></div>
      </a-col>

      <a-col class="gutter-row" :span="2">
        <div class="gutter-box"> <a-button type="primary">查询</a-button></div>
      </a-col>
</a-row>
  </div>
</template>

<script>
export default {
  data() {
    return {

    }
  },
  methods: {
       onChange(date, dateString) {
      console.log(date, dateString);
    }
  },
  components: {

  }
}
</script>

<style scoped>
.gutter-box {
  /* background: #00A0E9; */
  padding: 5px 0;
  font-size:18px;
  text-align: end;
  line-height: 40px;
}
.form-control{
  height:32px;
}
.picture{
  background: #fff;
  margin-top: -19px;
  margin-left: -39px;
}
</style>
