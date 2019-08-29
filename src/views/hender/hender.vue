<template>
 <div>
     <a-dropdown>
    <a class="ant-dropdown-link" >
      用户名 <a-icon type="down" style="fleat:right;"/>
    </a>
    <a-menu slot="overlay">
      <a-menu-item>
        <a href="javascript:;">修改密码</a>
      </a-menu-item>
    </a-menu>
  </a-dropdown>
  <a-button type="danger"><a-icon type="login" /></a-button>
 </div>
</template>

<script>
export default {
 data() {
 return {

 }
 },
 methods: {

 },
 components: {

 }
}
</script>

<style scoped>
.wai_{
    width:200px;
    /* padding: 4px; */
    border: 1px solid #cccccc;
}
.ant-dropdown-link{
    border: 1px solid #ccc;
    padding: 6px 60px 6px 6px;
    width:6px;
    margin-right: 20px;
    }
</style>
