<template>
<div class="dialog-demo">
  <h1 class="demo-title">Dialog对话框</h1>
  <div class="demo-ctn">
    <h2>基础用法</h2>
    <div class="demo-list">
      <div class="source">
        <Button>点击打开dialog</Button>
      </div>
      <div v-show="basicCodeShow" class="code-ctn">
        <p class="desc">使用<code>visible</code>来设置Dialog的显示和关闭，它接收<code>Boolean</code>。
          Dialog分为三部分：<code>title</code>、<code>body</code>和<code>footer</code>，<code>title</code>和<code>footer</code>需要具名<code>slot</code>。
        </p>

      </div>
      <div class="code-control" @click="toggle(1)">
        <span v-if="basicCodeShow">隐藏代码</span>
        <span v-else>显示代码</span>
      </div>
    </div>
  </div>
</div>
</template>

<script lang="ts">
import Button from '../libs/Button.vue'
import CodeItem from './CodeItem.vue'
import {
  ref
} from 'vue'
export default {
  components: {
    Button,
    CodeItem
  },
  setup() {
    const {
      basicCodeShow,
      toggle
    } = handleCodeShow()
    return {
      basicCodeShow,
      toggle
    }
  },
}

function handleCodeShow() {
  const basicCodeShow = ref(false)
  const disabledCodeShow = ref(false)
  const toggle = (type) => {
    switch (type) {
      case 1:
        basicCodeShow.value = !basicCodeShow.value
        break
      case 2:
        disabledCodeShow.value = !disabledCodeShow.value
    }
  }
  return {
    basicCodeShow,
    disabledCodeShow,
    toggle
  }
}
</script>
