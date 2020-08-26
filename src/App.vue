<template>
<router-view />
</template>

<script>
import {
  ref,
  provide
} from 'vue'
import router from './router/router'
export default {
  name: 'App',
  setup() {
    const width = document.documentElement.clientWidth
    let asideVisble = ref(width >= 700 ? true : false)
    provide('asideVisble', asideVisble)
    router.afterEach((to, from) => {
      if (width < 700) {
        asideVisble.value = false
      }
    })
  }
}
</script>
