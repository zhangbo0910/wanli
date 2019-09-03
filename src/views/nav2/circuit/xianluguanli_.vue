<template>
  <div>
      <a-row class="xianlu_">
      <a-col :span="2">车牌号:&nbsp;&nbsp;</a-col>
      <a-col :span="3">
        <a-input placeholder="单行输入" />
      </a-col>
       <a-col :span="2">线路名称:&nbsp;&nbsp;</a-col>
      <a-col :span="3">
        <a-input placeholder="单行输入" />
      </a-col>
      <a-col :span="2">区域类型:&nbsp;&nbsp;</a-col>
      <a-col :span="1">
        <a-dropdown>
          <a-dropdown>
            <a-menu slot="overlay" @click="handleMenuClick">
              <a-menu-item key="1">全部</a-menu-item>
              <a-menu-item key="2">线路</a-menu-item>
              <a-menu-item key="3">圆</a-menu-item>
              <a-menu-item key="4">矩形</a-menu-item>
              <a-menu-item key="5">多边形</a-menu-item>
            </a-menu>
            <a-button>
              矩形
              <a-icon type="down" />
            </a-button>
          </a-dropdown>
        </a-dropdown>
      </a-col>
      <a-col :span="9"></a-col>
      <a-col :span="2">
        <a-button type="primary">查询</a-button>
      </a-col>
    </a-row>
    <!-- 表格 -->
    <a-table :rowSelection="rowSelection" :columns="columns" :dataSource="data" bordered>
      <a slot="name" slot-scope="text" href="javascript:;">{{text}}</a>
      <span slot="tags" slot-scope="tags">
        <a-tag v-for="tag in tags" color="blue" :key="tag">{{tag}}</a-tag>
      </span>
    </a-table>
  </div>
</template>

<script>
const columns = [
  {
    title: "",
    dataIndex: "index",
    key: "key",
    scopedSlots: { customRender: "index" },
    width: "50px",
    align: "center"
  },
  {
    title: "车牌号",
    dataIndex: "num",
    key: "num",
    scopedSlots: { customRender: "num" },
    align: "center"
  },
  {
    title: "线路名称",
    dataIndex: "name",
    key: "name",
    scopedSlots: { customRender: "name" },
    align: "center"
  },
  {
    title: "所属公司",
    dataIndex: "company",
    key: "company",
    scopedSlots: { customRender: "company" },
    align: "center"
  },
  {
    title: "类型",
    dataIndex: "type",
    key: "type",
    scopedSlots: { customRender: "type" },
    align: "center"
  },
  {
    title: "操作",
    key: "tags",
    dataIndex: "tags",
    scopedSlots: { customRender: "tags" },
    align: "center"
  }
];

const data = [
  {
    key: `1`,
    index: `1`,
    num: `豫K11411`,
    name:`许昌—洛阳`,
    company: `客运十公司`,
    type: `线路`,
    tags: ["查看","复制", "删除"]
  },{
    key: `2`,
    index: `2`,
    num: `豫K11411`,
    name:`许昌—洛阳`,
    company: `客运十公司`,
    type: `线路`,
    tags: ["查看","复制", "删除"]
  },
  {
    key: `3`,
    index: `3`,
    num: `豫K11411`,
    name:`许昌—洛阳`,
    company: `客运十公司`,
    type: `线路`,
    tags: ["查看","复制", "删除"]
  }
];

export default {
  data() {
    return {
        data,
      columns
    }
  },
  methods: {
         handleMenuClick(e) {
      console.log("click", e);
    }
  },computed: {
    //单选框
    rowSelection() {
      const { selectedRowKeys } = this;
      return {
        onChange: (selectedRowKeys, selectedRows) => {
          console.log(
            `selectedRowKeys: ${selectedRowKeys}`,
            "selectedRows: ",
            selectedRows
          );
        },
        getCheckboxProps: record => ({
          props: {
            disabled: record.name === "Disabled User", // Column configuration not to be checked
            name: record.name
          }
        })
      };
    }
  },
  components: {

  }
}
</script>

<style scoped>
.xianlu_ {
  margin: 15px 0;
}
.xianlu_ div {
  text-align: end;
  font-size: 16px;
  line-height: 31px;
}

.editable-row-operations a {
  margin-right: 8px;
}
</style>
