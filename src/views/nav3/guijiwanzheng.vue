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
<!-- 表格 -->
   <a-table :columns="columns" :dataSource="data" bordered>
    <a slot="name" slot-scope="text" href="javascript:;">{{text}}</a>
  </a-table>
  </div>
</template>

<script>
const columns = [{
  title: '',
  dataIndex: 'index',
  key: 'key',
  scopedSlots: { customRender: 'index' },
  width:'50px',
  align:"center"
}, {
  title: '车牌号',
  dataIndex: 'num',
  key: 'num',
  scopedSlots: { customRender: 'num' },
  align:"center"
},{
  title: '公司名称',
  dataIndex: 'name',
  key: 'name',
  scopedSlots: { customRender: 'name' },
  align:"center"
}, {
  title: '车牌颜色',
  dataIndex:'color',
  key: 'color',
  scopedSlots: { customRender: 'color' },
  align:"center"
}, {
  title: '日期',
  dataIndex:'date_',
  key: 'date_',
  scopedSlots: { customRender: 'date_' },
  align:"center"
},{
  title: '不连续次数',
  dataIndex:'incontinuity_time',
  key: 'incontinuity_time',
  scopedSlots: { customRender: 'incontinuity_time' },
  align:"center"
},{
  title: 'GPS总数',
  dataIndex:'sum',
  key: 'sum',
  scopedSlots: { customRender: 'sum' },
  align:"center"
},{
  title: '不连续里程（公里）',
  dataIndex:'customRender_km',
  key: 'customRender_km',
  scopedSlots: { customRender_km: 'customRender_km' },
  align:"center"
},{
  title: '总里程（公里）',
  dataIndex:'sum_km',
  key: 'sum_km',
  scopedSlots: { customRender: 'sum_km' },
  align:"center"
},{
  title: '轨迹完整率',
  dataIndex:'null',
  key: 'null',
  scopedSlots: { customRender: 'null' },
  align:"center"
}];


const data = [];
for (let i = 0; i < 46; i++) {
  data.push({
    key: `${i}`,
    index: `${i+1}`,
    name: `襄县东方公交`,
    num:'豫K11112',
    color: `黄色`,
    date_:`2019-08-27`,
    incontinuity_time: `0`,
    sum:`0`,
    customRender_km:`0.00`,
    sum_km:`0.00`
  });
}



export default {
  data() {
    return {
     data,
     columns,
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
.ant-table-wrapper{
    margin-top: 20px;
}
</style>
