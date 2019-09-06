<template>
  <div>
     <a-row>
      <a-col :span="24" class="text_"><a-icon type="car" />&nbsp;&nbsp;规则分配-按车辆</a-col>
    </a-row>
    <a-row :gutter="16" class="content">
      <a-col class="gutter-row" :span="12">
        <div class="gutter-box">
          <div class="select">选择车辆</div>
          <div class="p_i"><p>查找车辆：</p><a-input placeholder="查找车辆"/></div>
        </div>
        <div class="control">

             <a-tree
              showLine
              :defaultExpandedKeys="['0-0-0']"
              @select="onSelect"
            >
              <a-tree-node key="0-0">
                <span slot="title" style="color: #1890ff">parent 1</span>
                <a-tree-node title="parent 1-0" key="0-0-0">
                  <a-tree-node title="leaf" key="0-0-0-0" />
                  <a-tree-node title="leaf" key="0-0-0-1" />
                  <a-tree-node title="leaf" key="0-0-0-2" />
                </a-tree-node>
                <a-tree-node title="parent 1-1" key="0-0-1">
                  <a-tree-node title="leaf" key="0-0-1-0" />
                </a-tree-node>
                <a-tree-node title="parent 1-2" key="0-0-2">
                  <a-tree-node title="leaf" key="0-0-2-0" />
                  <a-tree-node title="leaf" key="0-0-2-1" />
                </a-tree-node>
                 <a-tree-node title="parent 1-3" key="0-0-6">
                  <a-tree-node title="leaf" key="1-0-2-0" />
                  <a-tree-node title="leaf" key="2-0-2-1" />
                </a-tree-node>
                 <a-tree-node title="parent 1-4" key="0-0-3">
                  <a-tree-node title="leaf" key="3-0-2-0" />
                  <a-tree-node title="leaf" key="4-0-2-1" />
                  <a-tree-node title="leaf" key="5-0-2-1" />
                  <a-tree-node title="leaf" key="6-0-2-1" />
                  <a-tree-node title="leaf" key="7-0-2-1" />
                  <a-tree-node title="leaf" key="8-0-2-1" />
                </a-tree-node>
                 <a-tree-node title="parent 1-5" key="0-0-4">
                 <a-tree-node title="leaf" key="0-1-2-0" />
                 <a-tree-node title="leaf" key="0-2-2-1" />
                 <a-tree-node title="leaf" key="0-3-2-1" />
                 <a-tree-node title="leaf" key="0-4-2-1" />
                 <a-tree-node title="leaf" key="0-5-2-1" />
                 <a-tree-node title="leaf" key="0-6-2-1" />
                </a-tree-node>
              </a-tree-node>
            </a-tree>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="12">
        <div class="gutter-box">
          <div class="select">选择规则</div>
           <div class="p_i"><p>查找规则：</p><a-input placeholder="查找规则"/></div>
        </div>
        <div class="control">
            <!-- 树形控件2 -->
          <a-tree
            checkable
            @expand="onExpand"
            :expandedKeys="expandedKeys"
            :autoExpandParent="autoExpandParent"
            v-model="checkedKeys"
            @select="onSelect"
            :selectedKeys="selectedKeys"
            :treeData="treeData"
          />
        </div>
      </a-col>
    </a-row>
    <a-row>
      <a-col :span="12" :style="{'text-align':'center','line-height':'60px'}"><a-button>保存设置</a-button></a-col>
      <a-col :span="12"></a-col>
    </a-row>
     <a-row>
      <a-col :span="12" :style="{'text-align':'center'}">双击左边的公司或车辆出现右边的规则，勾选规则点击保存设置，规则只能分配给本公司车辆</a-col>
      <a-col :span="12"></a-col>
    </a-row>
  </div>
</template>

<script>
const treeData = [{
  title: '0-0',
  key: '0-0',
  children: [{
    title: '0-0-0',
    key: '0-0-0',
    children: [
      { title: '0-0-0-0', key: '0-0-0-0' },
      { title: '0-0-0-1', key: '0-0-0-1' },
      { title: '0-0-0-2', key: '0-0-0-2' },
    ],
  }, {
    title: '0-0-1',
    key: '0-0-1',
    children: [
      { title: '0-0-1-0', key: '0-0-1-0' },
      { title: '0-0-1-1', key: '0-0-1-1' },
      { title: '0-0-1-2', key: '0-0-1-2' },
    ],
  }, {
    title: '0-0-1',
    key: '0-0-1',
    children: [
      { title: '0-0-1-0', key: '0-0-1-0' },
      { title: '0-0-1-1', key: '0-0-1-1' },
      { title: '0-0-1-2', key: '0-0-1-2' },
    ],
  }, {
    title: '0-0-1',
    key: '0-0-1',
    children: [
      { title: '0-0-1-0', key: '0-0-1-0' },
      { title: '0-0-1-1', key: '0-0-1-1' },
      { title: '0-0-1-2', key: '0-0-1-2' },
    ],
  }, {
    title: '0-0-2',
    key: '0-0-2',
  }],
}, {
  title: '0-1',
  key: '0-1',
  children: [
    { title: '0-1-0-0', key: '0-1-0-0' },
    { title: '0-1-0-1', key: '0-1-0-1' },
    { title: '0-1-0-2', key: '0-1-0-2' },
  ],
}, {
  title: '0-2',
  key: '0-2',
}]


export default {
  data() {
    return {
       expandedKeys: ['0-0-0', '0-0-1'],
      autoExpandParent: true,
      checkedKeys: ['0-0-0'],
      selectedKeys: [],
      treeData,

    }
  },
  watch: {
    checkedKeys(val) {
      console.log('onCheck', val)
    }
  },
  methods: {
      onSelect (selectedKeys, info) {
      console.log('selected', selectedKeys, info)
    },
    //2
    onExpand (expandedKeys) {
      console.log('onExpand', expandedKeys)
      // if not set autoExpandParent to false, if children expanded, parent can not collapse.
      // or, you can remove all expanded children keys.
      this.expandedKeys = expandedKeys
      this.autoExpandParent = false
    },
    onCheck (checkedKeys) {
      console.log('onCheck', checkedKeys)
      this.checkedKeys = checkedKeys
    },
    onSelect (selectedKeys, info) {
      console.log('onSelect', info)
      this.selectedKeys = selectedKeys
    }

  },
  components: {

  }
}
</script>

<style scoped>
.text_{
  font-size:20px;
  font-weight: 900;
  border-bottom:3px solid #bbbbbb;
}
.select{
  font-size: 18px;
}
.p_i{
  width:40%;
  line-height:35px;
  overflow: hidden;
}
.p_i p{
  float: left;
}
.p_i .ant-input{
  width:50%;
  float: left;
}
.control{
  border: 1px solid #bbbbbb;
  height: 500px;
  overflow: auto;
}
.content{
  margin-top: 10px;
}
</style>
