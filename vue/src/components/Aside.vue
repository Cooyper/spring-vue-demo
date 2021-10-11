<template>
  <div>
    <el-menu style="width: 200px;min-height: calc(100vh - 50px);" default-active="user" class="el-menu-vertical-demo">
      <el-sub-menu index="1">
        <template #title>系统管理</template>
        <el-menu-item index="user" :route="{path:'/'}">用户管理</el-menu-item>

      </el-sub-menu>
      <el-menu-item index="data" :route="{path:'/'}">数据管理</el-menu-item>
    </el-menu>
  </div>
</template>

<script>
export default {
  name: "Aside",
  // data:{
  //   return{
  //     user: {},
  //     path: this.$route.path   // 设置默认高亮的菜单
  //   }
  // },
  // created() {
  //   let userStr = sessionStorage.getItem("user") || "{}"
  //   this.user = JSON.parse(userStr)
  //
  //   // 请求服务端，确认当前登录用户的 合法信息
  //   request.get("/user/" + this.user.id).then(res => {
  //     if (res.code === '0') {
  //       this.user = res.data
  //     }
  //   })
  // }
}
</script>

<style scoped>

</style>