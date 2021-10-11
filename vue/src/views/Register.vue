<template>
  <div style="width: 100%;height: 100vh;background-color:darkslateblue;overflow: hidden;">

    <div style="width: 400px;margin:150px auto;">
      <div style="color: #cccccc;font-size: 30px;text-align: center;padding: 30px;">欢迎注册</div>
      <el-form ref="form" :model="form" size="normal" :rules="rules">
        <el-form-item prop="username">
          <el-input v-model="form.username" prefix-icon="el-icon-user-solid" placeholder="Please input username"></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input v-model="form.password" prefix-icon="el-icon-lock" placeholder="Please input password" show-password></el-input>
        </el-form-item>
        <el-form-item prop="confirm">
          <el-input v-model="form.confirm" prefix-icon="el-icon-lock" placeholder="Please input password" show-password></el-input>
        </el-form-item>
        <el-form-item>
          <el-button style="width: 100%;" type="primary" @click="register">注 册</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
import request from "@/utils/request";
import { ElMessage } from 'element-plus'

export default {
  name: "Register",
  data(){
    return{
      form:{},
      rules: {
        username: [
          {
            required: true,
            message: '请输入用户名',
            trigger: 'blur',
          },
        ],
        password: [
          {
            required: true,
            message: '请输入密码',
            trigger: 'blur',
          },
        ],
        confirm: [
          {
            required: true,
            message: '请确认密码',
            trigger: 'blur',
          },
        ],
      }
    }
  },
  methods:{
    register(){

      if(this.form.password !== this.form.confirm){
        ElMessage({
          message: '2次密码输入不一致！',
          type: 'error',
        })
        return
      }

      this.$refs['form'].validate((valid)=> {
        if (valid) {
          request.post("/api/user/register",this.form).then(res=>{
            if(res.code === '0'){
              ElMessage({
                message: '注册成功！',
                type: 'success',
              })
              this.$router.push("/login");  //注册成功后进行的页面跳转，跳转到登录页面
            }else{
              ElMessage({
                message: res.msg,
                type: 'error',
              })
            }
          })
        }
      })
    },
  }
}
</script>

<style scoped>

</style>