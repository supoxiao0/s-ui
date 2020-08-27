<template>
<div class="button-demo">
  <div class="size-demo">
    <p>不同尺寸</p>
    <div>
      <Button size="big">大按钮</Button>
      <Button size="medium">中等按钮</Button>
      <Button size="small">小按钮</Button>
    </div>
  </div>
</div>
</template>

<script lang="ts">
import Button from '../libs/Button.vue'
export default {
  components: {
    Button
  }
}
</script>

<style lang="scss" scoped>
  
</style>
