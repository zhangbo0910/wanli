<template>
 <div>
     <a-dropdown>
    <a class="ant-dropdown-link" >
      {{username}} <a-icon type="down" style="fleat:right;"/>
    </a>
    <a-menu slot="overlay">
      <a-menu-item>
        <a href="javascript:;" @click="showModal2">修改密码</a>
              <a-modal
            title="修改密码"
           v-model="visible2"
           @ok="handleOk_t"
            okText="确认"
          cancelText="取消"
          >
       
            <a-form
    id="components-form-demo-normal-login"
    :form="form"
    class="login-form"
    @submit="handleSubmit"
  >
    <a-form-item>
        <p>请输入旧的密码:</p>
      <a-input
        v-decorator="[
          'password',
          { rules: [{ required: true, message: '请输入正确的密码！' }] }
        ]"
        type="password"
        placeholder="Password"
      >
        <a-icon
          slot="prefix"
          type="lock"
          style="color: rgba(0,0,0,.25)"
        />
      </a-input>
    </a-form-item>

     <a-form-item>
       <p>请输入新的密码:</p>
      <a-input
        v-decorator="[
          'new_password',
          { rules: [{ required: true, message: '请输入正确的密码！' }] }
        ]"
        type="password"
        placeholder="Password"
      >
        <a-icon
          slot="prefix"
          type="lock"
          style="color: rgba(0,0,0,.25)"
        />
      </a-input>
    </a-form-item>
    <a-form-item>
    <a-button
        type="primary"
        html-type="submit"
        class="login-form-button"
      >
        提交
      </a-button>
    </a-form-item>
  </a-form>






          </a-modal>
      </a-menu-item>
    </a-menu>
  </a-dropdown>
  <a-button type="danger"  @click="showModal"><a-icon type="login" /></a-button>
   <a-modal
      v-model="visible"
      @ok="handleOk"
        okText="确认"
      cancelText="取消"
    >
      <p>确认退出当前账号吗？</p>
    </a-modal>
 </div>
</template>

<script>
export default {
    beforeCreate () {
    this.form = this.$form.createForm(this);
  },
 data() {
 return {
    name:"",
    visible: false,
    visible2:false
 }
 },
 computed:{
      username: function () {
       var bbb = JSON.parse(sessionStorage.getItem('userinfo'));
       return this.name=bbb.userName;
    }
 },
 methods: {
    showModal() {
      this.visible = true
    },
    handleOk(e) {
      console.log(e);
      this.visible = false;
      sessionStorage.removeItem('userinfo');
      this.$router.push('/');
    },
    showModal2(){
      this.visible2 = true
    },
    handleOk_t(e){
       console.log(e);
      this.visible2 = false;
    },
    //修改密码
      handleSubmit (e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values);
        }
      });
    }

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
