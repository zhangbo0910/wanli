<template>
<div :style="{overflow:'hidden'}">
  <div class="login_box">
      <div class="logo_box">
          <img src="../../assets/img/logo.png" alt="出错了">
      </div>
      <div class="input_box">
               <a-form
    id="components-form-demo-normal-login"
    :form="form"
    class="login-form"
    @submit="handleSubmit"
  >
    <!-- 账号 -->
    <a-form-item>
      <a-input
        v-decorator="[
          'userName',
          { rules: [{ required: true, message: '请输入正确的用户名！' }] }
        ]"
        placeholder="用户名"
      >
        <a-icon
          slot="prefix"
          type="user"
          style="color: rgba(0,0,0,.25)"
        />
      </a-input>
    </a-form-item>
    <!-- 密码 -->
    <a-form-item>
      <a-input
        v-decorator="[
          'password',
          { rules: [{ required: true, message: '请输入正确的密码！' }] }
        ]"
        type="password"
        placeholder="密码"
      >
        <a-icon
          slot="prefix"
          type="lock"
          style="color: rgba(0,0,0,.25)"
        />
      </a-input>
    </a-form-item>
    <!-- 验证码 -->
      <a-form-item>
        <a-col :span="12">
          <a-input
            v-decorator="[
              'captcha',
              {rules: [{ required: true, message: '请输入正确的验证码' }]}
            ]"
             placeholder="验证码"
          />
        </a-col>
        <a-col :span="12">   <!-- 验证码 -->
          <a-button class="code_y" @click="refreshCode">
            <Sidentify :identifyCode='identifyCode'></Sidentify>
            </a-button>
        </a-col>
    </a-form-item>
    <!-- 登录按钮 -->
    <a-form-item>
      <a-button
        type="primary"
        html-type="submit"
        class="login-form-button"
      >
        登录
      </a-button>
    </a-form-item>
  </a-form>
  </div>
  </div>
  </div>
</template>

<script>
import Sidentify from './identify/identify.vue'
export default {
    beforeCreate () {
    this.form = this.$form.createForm(this);
  },
  data() {
    return {
      identifyCodes: "1234567890",
      identifyCode: ""
    }
  },
  mounted() {
   this.identifyCode = "";
    this.makeCode(this.identifyCodes, 4);
  },
  methods: {

       handleSubmit (e) {
        e.preventDefault();
        this.form.validateFields((err, values) => {
            if (!err) {
              //  const hide = this.$message.loading('登陆中...', 0);
              // setTimeout(hide, 2500);
            console.log('表单值为：',values);
            sessionStorage.setItem('userinfo',JSON.stringify(values));

             this.$message.success(values.userName+'登陆成功！');
             this.$router.push('/home')
            }else{
               this.$message.error('登录失败');
            }
        }); 
    },


      //验证码
     randomNum(min, max) {
      return Math.floor(Math.random() * (max - min) + min);
    },
    refreshCode() {
      this.identifyCode = "";
      this.makeCode(this.identifyCodes, 4);
    },
    makeCode(o, l) {
      for (let i = 0; i < l; i++) {
        this.identifyCode += this.identifyCodes[
          this.randomNum(0, this.identifyCodes.length)
        ];
      }
      console.log(this.identifyCode);
    }


  },
  components: {
    Sidentify
  }
}
</script>

<style scoped>
    #components-form-demo-normal-login .login-form {
    max-width: 300px;
    }
    #components-form-demo-normal-login .login-form-forgot {
    float: right;
    }
    #components-form-demo-normal-login .login-form-button {
    width: 100%;
    }
    .login_box{
        width:500px;
        margin: 180px auto 0;
        /* border: 1px solid #cccccc; */
        overflow: hidden;
        background: rgba(0,0,0,.3);
        border-radius: 10px;
    }
    .code_y{
        margin-left:70px;
        height: 40px;
        padding: 0;
    }
    .logo_box{
        margin-bottom: 40px;
    }
    .logo_box>img{
        width:500px;
    }
    .input_box{
        padding: 20px;
    }
    .ant-input-affix-wrapper{
        height:40px;
    }
    .login-form-button,.ant-input{
        height: 40px;
    }
</style>
