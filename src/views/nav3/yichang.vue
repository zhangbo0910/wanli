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
        <!-- 表格   调分页器每页显示条数 -->
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
},{
  title: '车牌颜色',
  dataIndex:'color',
  key: 'color',
  scopedSlots: { customRender: 'color' },
  align:"center"
},{
  title: '报警开始时间',
  dataIndex:'start_time',
  key: 'start_time',
  scopedSlots: { customRender: 'start_time' },
  align:"center"
}, {
  title: '报警结束时间',
  key: 'end_time',
  dataIndex: 'end_time',
  scopedSlots: { customRender: 'end_time' },
  align:"center"
}, {
  title: '报警时长',
  key: 'duration',
  dataIndex: 'duration',
  scopedSlots: { customRender: 'duration' },
  align:"center"
}, {
  width:'250px',
  title: '报警开始地点',
  key: 'Start_location',
  dataIndex: 'Start_location',
  scopedSlots: { customRender: 'Start_location' },
  align:"center"
}, {
  width:'250px',
  title: '报警结束地点',
  key: 'end_location',
  dataIndex: 'end_location',
  scopedSlots: { customRender: 'end_location' },
  align:"center"
}];


const data = [];
for (let i = 0; i < 46; i++) {
  data.push({
     key:`${i}`,
    index: `${i+1}`,
    name: `周口太康公司`,
    num: `豫K11112`,
    color: `黄色`,
    start_time:`2019-08-14 18:04:33`,
    end_time:`2019-08-14 18:04:46`,
    duration:`00:00:13`,
    Start_location:`湖北省孝感市孝南区G4(京港澳高速)杨家寨西北224米`,
    end_location:`湖北省孝感市孝南区G4(京港澳高速)上李家湾西南419米`
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
    margin-bottom: 50px;
}
</style>
