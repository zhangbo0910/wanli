<template>
  <div>
<a-row class="picture">
      <a-col class="gutter-row" :span="4">
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
    <a-col class="gutter-row" :span="2">
        <div class="gutter-box">
          <a-input placeholder="单行输入"/>
        </div>
      </a-col>

      <a-col class="gutter-row" :span="2">
        <div class="gutter-box">起始时间:</div>
      </a-col>
     <a-col class="gutter-row" :span="4">
        <div class="gutter-box"><a-range-picker @change="onChange" /></div>
      </a-col>

        <a-col class="gutter-row" :span="4">
        <div class="gutter-box">
          处理状态:
          <select  class="form-control">
             <option>全部</option>
             <option>处理中</option>
             <option>处理完毕</option>
          </select>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="4">
        <div class="gutter-box">
          告警类型：
          <select  class="form-control">
             <option>全部</option>
             <option>超速报警</option>
             <option>疲劳驾驶报警</option>
          </select>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="2">
        <div class="gutter-box"> <a-button type="primary">解除</a-button></div>
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
},{
  title: '公司名称',
  dataIndex: 'name',
  key: 'name',
  scopedSlots: { customRender: 'name' },
  align:"center"
}, {
  title: '车牌号',
  dataIndex: 'num',
  key: 'num',
  scopedSlots: { customRender: 'num' },
  align:"center"
}, {
  title: '告警类型',
  dataIndex:'type',
  key: 'type',
  scopedSlots: { customRender: 'type' },
  align:"center"
}, {
  title: '告警来源',
  dataIndex:'source',
  key: 'source',
  scopedSlots: { customRender: 'source' },
  align:"center"
}, {
  title: '告警内容',
  dataIndex:'content',
  key: 'content',
  scopedSlots: { customRender: 'content' },
  align:"center"
},{
  title: '告警车速（公里/时）',
  dataIndex:'speed',
  key: 'speed',
  scopedSlots: { customRender: 'speed' },
  align:"center",
  width:'110px'
},{
  title: '限速（公里/时）',
  dataIndex:'rate_limiting',
  key: 'rate_limiting',
  scopedSlots: { customRender: 'rate_limiting' },
  align:"center",
   width:'90px'
},{
  title: '告警位置',
  dataIndex:'location',
  key: 'location',
  scopedSlots: { customRender_km: 'location' },
  align:"center"
},{
  title: '处理状态',
  dataIndex:'state',
  key: 'state',
  scopedSlots: { customRender_km: 'state' },
  align:"center"
},{
  title: '开始时间',
  dataIndex:'start_time',
  key: 'start_time',
  scopedSlots: { customRender_km: 'start_time' },
  align:"center"
},{
  title: '结束时间',
  dataIndex:'end_time',
  key: 'end_time',
  scopedSlots: { customRender_km: 'end_time' },
  align:"center"
}];


const data = [];
for (let i = 0; i < 46; i++) {
  data.push({
       key: `${i}`,
    index: `${i+1}`,
    name: `客运五公司`,
    num:'豫K11112',
    type: `超速报警`,
    source:`平台报警`,
    content: `超速`,
    speed:`95`,
    rate_limiting:`90`,
    location:`杨金路`,
    state:`未处理`,
    start_time:`2019-08-27 16：26：33`,
    end_time:`2019-08-27 16：45：88`
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
  font-size:13px;
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
