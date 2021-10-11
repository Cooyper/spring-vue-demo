<template>

  <div>
    <router-view />
  </div>

</template>

<script>
import {defineComponent} from 'vue'
import {ElConfigProvider} from 'element-plus'
import zhCn from 'element-plus/lib/locale/lang/zh-cn'

export default {
  name: "App ",
  setup() {
    return {
      locale: zhCn,
    }
  },
}

</script>
