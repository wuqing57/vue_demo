<template>
<div>
  <form  v-if="!isLog">
    <div>用户名：</div>
    <el-form-item label="用户名">
      <el-input v-model="name" placeholder="请输入内容"></el-input>
    </el-form-item>
<!--    <div class="line-margin-top">-->
<!--    <el-form-item label="用户名">-->
<!--      <el-input v-model="name" placeholder="请输入内容"></el-input>-->
<!--    </el-form-item>-->
<!--    </div>-->
    <div>密码：</div>
    <el-input show-password v-model="password" placeholder="请输入内容"></el-input>
    <div>
    <button type="button" @click="login()">登录</button>
    <button type="button" @click="register()">注册</button>
    </div>
  </form>
  <form v-else>
    <div>用户名：</div>
    <input type="text" v-model="name">
    <div>密码：</div>
    <input type="password" v-model="password">
    <div>再次输入密码：</div>
    <input type="password" v-model="repeat">
    <div >
    <button type="button" @click="add()">注册</button>
    <button type="button" @click="cancel()">返回</button>
    </div>
  </form>
</div>
</template>

<script>
    export default {
      name: "Login",
      data (){
        return {
          isLog : false,
          name : "",
          password:"",
          repeat:""
        }
      },
      methods:{
        login(){
          if(localStorage.getItem("name")===this.name &&localStorage.getItem("password")===this.password){
            this.name=""
            this.password=""
            this.$router.push("/welcome")
          }else {
            this.name=""
            this.password=""
            alert("用户名密码错误")
          }
        },
        register(){

          this.isLog = true
          // alert(this.isLog)
        },
        add(){
          if(this.password === this.repeat){
            localStorage.setItem("name",this.name)
            localStorage.setItem("password",this.password)
            this.name=""
            this.password=""
            this.isLog = false
          }else {
            alert("两次密码输入不一致")
          }

        },
        cancel(){
          this.isLog=false
        }
      }
    }
</script>

<style scoped>

</style>
