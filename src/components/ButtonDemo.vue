<template>
<div class="button-demo">
  <h1 class="demo-title">Button按钮</h1>
  <div class="demo-ctn">
    <h2>基础用法</h2>
    <div class="demo-list">
      <div class="source">
        <Button theme="default">默认按钮</Button>
        <Button theme="success">成功按钮</Button>
        <Button theme="warning">警告按钮</Button>
        <Button theme="danger">危险按钮</Button>
        <Button theme="plain">朴素按钮</Button>
      </div>
      <div v-show="themeCodeShow" class="code-ctn">
        <p class="desc">使用<code>theme</code>来定义Button的主题
        </p>
        <code class="code">
          <span class="code-span">
            <span class="code-span-tag">&lt;</span>
            <span class="code-span-name">s-button </span>
            <span class="code-span-attr">theme=</span>
            <span class="code-span-string">"default"</span>
            <span class="code-span-tag">&gt;</span>
            <span>默认按钮</span>
            <span class="code-span-tag">&lt;</span>
            <span class="code-span-name">/s-button</span>
            <span class="code-span-tag">&gt;</span>
          </span>
          <span class="code-span">
            <span class="code-span-tag">&lt;</span>
            <span class="code-span-name">s-button </span>
            <span class="code-span-attr">theme=</span>
            <span class="code-span-string">"success"</span>
            <span class="code-span-tag">&gt;</span>
            <span>成功按钮</span>
            <span class="code-span-tag">&lt;</span>
            <span class="code-span-name">/s-button</span>
            <span class="code-span-tag">&gt;</span>
          </span>
          <span class="code-span">
            <span class="code-span-tag">&lt;</span>
            <span class="code-span-name">s-button </span>
            <span class="code-span-attr">theme=</span>
            <span class="code-span-string">"warning"</span>
            <span class="code-span-tag">&gt;</span>
            <span>警告按钮</span>
            <span class="code-span-tag">&lt;</span>
            <span class="code-span-name">/s-button</span>
            <span class="code-span-tag">&gt;</span>
          </span>
          <span class="code-span">
            <span class="code-span-tag">&lt;</span>
            <span class="code-span-name">s-button </span>
            <span class="code-span-attr">theme=</span>
            <span class="code-span-string">"danger"</span>
            <span class="code-span-tag">&gt;</span>
            <span>危险按钮</span>
            <span class="code-span-tag">&lt;</span>
            <span class="code-span-name">/s-button</span>
            <span class="code-span-tag">&gt;</span>
          </span>
          <span class="code-span">
            <span class="code-span-tag">&lt;</span>
            <span class="code-span-name">s-button </span>
            <span class="code-span-attr">theme=</span>
            <span class="code-span-string">"plain"</span>
            <span class="code-span-tag">&gt;</span>
            <span>朴素按钮</span>
            <span class="code-span-tag">&lt;</span>
            <span class="code-span-name">/s-button</span>
            <span class="code-span-tag">&gt;</span>
          </span>
        </code>
      </div>
      <div class="code-control" @click="toggle(1)">
        <span v-if="themeCodeShow">隐藏代码</span>
        <span v-else>显示代码</span>
      </div>
    </div>
  </div>
  <div class="demo-ctn">
    <h2>不同尺寸</h2>
    <div class="demo-list">
      <Button size="big">大按钮</Button>
      <Button size="medium">中等按钮</Button>
      <Button size="small">小按钮</Button>
    </div>
  </div>
</div>
</template>

<script lang="ts">
import Button from '../libs/Button.vue'
import {
  ref
} from 'vue'
export default {
  components: {
    Button
  },
  setup() {
    const themeCodeShow = ref(false)
    const toggle = (type) => {
      switch (type) {
        case 1:
          themeCodeShow.value = !themeCodeShow.value
          break;
      }
    }
    return {
      themeCodeShow,
      toggle
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
