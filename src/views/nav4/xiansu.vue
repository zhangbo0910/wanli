<template>
  <div>
<a-row class="picture">
      <a-col class="gutter-row" :span="2">
        <div class="gutter-box">
          <span>车牌号：</span>
        </div>
      </a-col>
    <a-col class="gutter-row" :span="5">
        <div class="gutter-box">
          <a-input placeholder="单行输入"/>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="2">
        <div class="gutter-box"> <a-button type="primary">查询</a-button></div>
      </a-col>
       <a-col class="gutter-row" :span="2">
        <div class="gutter-box"> <a-button type="primary">添加</a-button></div>
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
}, {
  title: '车牌颜色',
  dataIndex:'color',
  key: 'color',
  scopedSlots: { customRender: 'color' },
  align:"center"
},{
  title: '最高速度（公里/时）',
  dataIndex:'speed',
  key: 'speed',
  scopedSlots: { customRender: 'speed' },
  align:"center"
},{
  title: '超速持续时间（秒）',
  dataIndex:'time',
  key: 'time',
  scopedSlots: { customRender: 'time' },
  align:"center"
},{
  title: '跨省线路',
  dataIndex:'circuit',
  key: 'circuit',
  scopedSlots: { customRender: 'circuit' },
  align:"center"
},{
  title: '操作',
  dataIndex:'operation',
  key: 'operation',
  scopedSlots: { customRender: 'operation' },
  align:"center"
}];


const data = [];
for (let i = 0; i < 46; i++) {
  data.push({
       key: `${i}`,
    index: `${i+1}`,
    num:'豫K11112',
    color: `黄色`,
    speed:`126`,
    time: `13`,
    circuit:`否`,
    operation:`修改`
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
