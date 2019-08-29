<template>
  <div>
    <a-row>
      <a-col :span="24" class="border">
        <a-button>线路管理</a-button>
        <a-button type="primary">车辆绑定路线查询</a-button>
      </a-col>
    </a-row>
    <a-row class="xianlu_">
      <a-col :span="2">线路名称:&nbsp;&nbsp;</a-col>
      <a-col :span="6"><a-input placeholder="单行输入"/></a-col>
      <a-col :span="2">区域类型:&nbsp;&nbsp;</a-col>
      <a-col :span="1"><a-dropdown>
    <a-dropdown>
      <a-menu slot="overlay" @click="handleMenuClick">
        <a-menu-item key="1">全部</a-menu-item>
        <a-menu-item key="2">线路</a-menu-item>
        <a-menu-item key="3">圆</a-menu-item>
        <a-menu-item key="4">矩形</a-menu-item>
        <a-menu-item key="5">多边形</a-menu-item>
      </a-menu>
      <a-button>
        矩形 <a-icon type="down" />
      </a-button>
    </a-dropdown>
  </a-dropdown></a-col>
  <a-col :span="9"></a-col>
      <a-col :span="2"><a-button type="primary">查询</a-button></a-col>
      <a-col :span="2"><a-button type="primary">添加</a-button></a-col>
    </a-row>
    <!-- 表格 -->
    <a-table :columns="columns" :dataSource="data" bordered>
    <template v-for="col in ['name', 'age', 'address']" :slot="col" slot-scope="text, record, index">
      <div :key="col">
        <a-input
          v-if="record.editable"
          style="margin: -5px 0"
          :value="text"
          @change="e => handleChange(e.target.value, record.key, col)"
        />
        <template v-else>{{text}}</template>
      </div>
    </template>
    <template slot="operation" slot-scope="text, record, index">
      <div class='editable-row-operations'>
        <span v-if="record.editable">
          <a @click="() => save(record.key)">Save</a>
          <a-popconfirm title='Sure to cancel?' @confirm="() => cancel(record.key)">
            <a>Cancel</a>
          </a-popconfirm>
        </span>
        <span v-else>
          <a @click="() => edit(record.key)">Edit</a>
        </span>
      </div>
    </template>
  </a-table>
  </div>
</template>

<script>
const columns = [{
  title: '线路名称',
  dataIndex: 'xianlumingcheng',
  width: '25%',
  scopedSlots: { customRender: '线路名称' },
}, {
  title: '线路类型',
  dataIndex: 'age',
  width: '15%',
  scopedSlots: { customRender: '线路类型' },
}, {
  title: '最高速度（km/h）',
  dataIndex: 'address',
  width: '40%',
  scopedSlots: { customRender: '最高速度（km/h）' },
}, {
  title: '开始时间  ',
  dataIndex: 'operation',
  scopedSlots: { customRender: '开始时间' },
}]

const data = []
for (let i = 0; i < 100; i++) {
  data.push({
    key: i.toString(),
    name: `Edrward ${i}`,
    age: 32,
    address: `London Park no. ${i}`,
  })
}

export default {
  data() {
    this.cacheData = data.map(item => ({ ...item }))
    return {
      data,
      columns
    }
  },
  methods: {
     handleMenuClick(e) {
      console.log('click', e);
    },
    //表格
     handleChange (value, key, column) {
      const newData = [...this.data]
      const target = newData.filter(item => key === item.key)[0]
      if (target) {
        target[column] = value
        this.data = newData
      }
    },
    edit (key) {
      const newData = [...this.data]
      const target = newData.filter(item => key === item.key)[0]
      if (target) {
        target.editable = true
        this.data = newData
      }
    },
    save (key) {
      const newData = [...this.data]
      const target = newData.filter(item => key === item.key)[0]
      if (target) {
        delete target.editable
        this.data = newData
        this.cacheData = newData.map(item => ({ ...item }))
      }
    },
    cancel (key) {
      const newData = [...this.data]
      const target = newData.filter(item => key === item.key)[0]
      if (target) {
        Object.assign(target, this.cacheData.filter(item => key === item.key)[0])
        delete target.editable
        this.data = newData
      }
    }

  },
  components: {

  }
}
</script>

<style scoped>
  .border{
    border-bottom: 4px solid #bebebe;
    padding-left:60px; 
  }
  .border .ant-btn{
      height:40px;
  }
  .xianlu_{
    margin:15px 0;
  }
  .xianlu_ div{
    text-align: end;
    font-size:16px;
    line-height:31px; 
  }

  .editable-row-operations a {
  margin-right: 8px;
}
</style>
