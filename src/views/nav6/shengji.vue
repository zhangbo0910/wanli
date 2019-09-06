<template>
  <div>
<a-row :gutter="15" class="picture">
      <a-col class="gutter-row" :span="2">
        <div class="gutter-box">
          <span>任务名称：</span>
        </div>
      </a-col>
    <a-col class="gutter-row" :span="3">
        <div class="gutter-box">
          <a-input placeholder="任务名称"/>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="2">
        <div class="gutter-box"> <a-button type="primary">所有任务</a-button></div>
      </a-col>
      <a-col class="gutter-row" :span="2">
        <div class="gutter-box"> <a-button type="primary">添加</a-button></div>
      </a-col>
</a-row>
<!-- 表格 -->
   <a-table :columns="columns" :dataSource="data" bordered>
    <a slot="name" slot-scope="text" href="javascript:;">{{text}}</a>
    <span slot="tags" slot-scope="tags">
        <div v-for="tag in tags" :key="tag"  class="tag_">
            <a-icon type="pie-chart" theme="twoTone" :style="{ fontSize: '30px' }" @click="pie_chart"/>
            <a-icon type="down-circle" theme="twoTone"  :style="{ fontSize: '30px' }" @click="down_circle"/>
            <a-icon type="edit" theme="twoTone"  :style="{ fontSize: '30px' }" @click="edit"/>
            <a-icon type="delete" theme="twoTone"  :style="{ fontSize: '30px' }" @click="deletes"/>
        </div>
    </span>
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
  title: '任务名称',
  dataIndex: 'name',
  key: 'name',
  scopedSlots: { customRender: 'name' },
  align:"center"
}, {
  title: '升级类型',
  dataIndex: 'type',
  key: 'type',
  scopedSlots: { customRender: 'type' },
  align:"center"
},{
  title: '目标版本号',
  dataIndex:'b_num',
  key: 'b_num',
  scopedSlots: { customRender: 'b_num' },
  align:"center"
},{
  title: '操作',
  key: 'tags',
  dataIndex: 'tags',
  scopedSlots: { customRender: 'tags' },
  align:"center"
}];


const data = [];
for (let i = 0; i < 4; i++) {
  data.push({
    key:`${i}`,
    index: `${i+1}`,
    name: `驾驶辅助`,
    type: `高级驾驶辅助`,
    b_num: `1.1.1`,
    tags:[1]
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
        },
        pie_chart(){
           this.$message.info('分配升级任务 驾驶辅助');
        },
        down_circle(){
            this.$message.info('查看 任务升级配置');
        },
        edit(){
            this.$message.info('修改 任务升级配置');
         },
        deletes(){
            this.$message.info('删除');
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
.tag_{
  display: flex;
}
.tag_ i{
  flex: 1;
}
</style>
