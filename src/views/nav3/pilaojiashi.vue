<template>
  <div>
    <a-row :gutter="15" class="picture">
      <a-col class="gutter-row" :span="5">
        <div class="gutter-box">
          公司名称：
          <select class="form-control">
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
          <a-input placeholder="单行输入" />
        </div>
      </a-col>

      <a-col class="gutter-row" :span="2">
        <div class="gutter-box">起始时间:</div>
      </a-col>
      <a-col class="gutter-row" :span="5">
        <div class="gutter-box">
          <a-range-picker @change="onChange" />
        </div>
      </a-col>

      <a-col class="gutter-row" :span="2">
        <div class="gutter-box">
          <a-button type="primary">查询</a-button>
        </div>
      </a-col>
    </a-row>
    <!-- 表格 -->
    <a-table :columns="columns" :dataSource="data" bordered>
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
    title: "公司名称",
    dataIndex: "name",
    key: "name",
    //   scopedSlots: { customRender: 'name' },
    align: "center"
  },
  {
    title: "车牌号",
    dataIndex: "code",
    key: "code",
    scopedSlots: { customRender: "type" },
    align: "center"
  },
  {
    title: "车牌颜色",
    dataIndex: "color",
    key: "color",
    scopedSlots: { customRender: "color" },
    align: "center"
  },
  {
    title: "报警次数",
    dataIndex: "num",
    key: "num",
    scopedSlots: { customRender: "num" },
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
const data = [];
for (let i = 0; i < 46; i++) {
  data.push({
    key:`${i}`,
    name: `客运五公司`,
    index: `${i + 1}`,
    code: `豫K11113`,
    color: `黄色`,
    num: `1`,
    tags: ["详情"]
  });
}

export default {
  data() {
    return {
      data,
      columns
    };
  },
  methods: {
    onChange(date, dateString) {
      console.log(date, dateString);
    }
  },
  components: {}
};
</script>

<style scoped>
.gutter-box {
  /* background: #00A0E9; */
  padding: 5px 0;
  font-size: 18px;
  text-align: end;
  line-height: 40px;
}
.form-control {
  height: 32px;
}
.picture {
  background: #fff;
  margin-top: -19px;
  margin-left: -39px;
}
.ant-table-wrapper {
  margin-top: 20px;
}
</style>
