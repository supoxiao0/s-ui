<template>
<div class="button-demo">
  <h1 class="demo-title">Button按钮</h1>
  <div class="demo-ctn">
    <h2>基础用法</h2>
    <div class="demo-list">
      <div class="source">
        <Button v-for="code in themeCodeInfo.valueList" :key="code.string" :theme="code.string">{{code.name}}</Button>
      </div>
      <div v-show="themeCodeShow" class="code-ctn">
        <p class="desc">使用<code>theme</code>来定义Button的主题
        </p>
        <CodeItem :codeInfo="themeCodeInfo" />
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
      <div class="source">
        <Button v-for="code in sizeCodeInfo.valueList" :key="code.string" :size="code.string">{{code.name}}</Button>
      </div>
      <div v-show="sizeCodeShow" class="code-ctn">
        <p class="desc">使用<code>size</code>来定义Button的大小
        </p>
        <CodeItem :codeInfo="sizeCodeInfo" />
      </div>
      <div class="code-control" @click="toggle(2)">
        <span v-if="sizeCodeShow">隐藏代码</span>
        <span v-else>显示代码</span>
      </div>
    </div>
  </div>
  <div class="demo-ctn">
    <h2>禁用状态</h2>
    <div class="demo-list">
      <div class="source">
        <Button disabled>默认按钮</Button>
      </div>
      <div v-show="disabledCodeShow" class="code-ctn">
        <p class="desc">使用<code>disabled</code>来定义Button是否可用，它接受一个<code>Boolean</code>值
        </p>
        <CodeItem :codeInfo="disabledCodeInfo" />
      </div>
      <div class="code-control" @click="toggle(3)">
        <span v-if="disabledCodeShow">隐藏代码</span>
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
  ref,
  reactive
} from 'vue'
export default {
  components: {
    Button,
    CodeItem
  },
  setup() {
    // 管理显示和隐藏
    const {
      themeCodeShow,
      sizeCodeShow,
      disabledCodeShow,
      toggle
    } = handleCodeShow()
    // 初始化数据
    const {
      sizeCodeInfo,
      themeCodeInfo,
      disabledCodeInfo
    } = initData()

    const onClick = () => {
      console.log('hi')
    }
    return {
      onClick,
      themeCodeShow,
      sizeCodeShow,
      disabledCodeShow,
      sizeCodeInfo,
      themeCodeInfo,
      disabledCodeInfo,
      toggle
    }
  },
}

function handleCodeShow() {
  const themeCodeShow = ref(false)
  const sizeCodeShow = ref(false)
  const disabledCodeShow = ref(false)
  const toggle = (type) => {
    switch (type) {
      case 1:
        themeCodeShow.value = !themeCodeShow.value
        break
      case 2:
        sizeCodeShow.value = !sizeCodeShow.value
        break
      case 3:
        disabledCodeShow.value = !disabledCodeShow.value
        break
    }
  }
  return {
    themeCodeShow,
    sizeCodeShow,
    disabledCodeShow,
    toggle
  }
}

function initData() {
  const themeCodeInfo = reactive({
    tag: 's-button',
    attr: 'theme',
    valueList: [{
        name: '默认按钮',
        string: 'default'
      },
      {
        name: '成功按钮',
        string: 'success'
      },
      {
        name: '警告按钮',
        string: 'warning'
      },
      {
        name: '危险按钮',
        string: 'danger'
      },
      {
        name: '朴素按钮',
        string: 'plain'
      }
    ]
  })
  const sizeCodeInfo = reactive({
    tag: 's-button',
    attr: 'size',
    valueList: [{
        name: '大按钮',
        string: 'big'
      },
      {
        name: '默认大小',
        string: 'medium'
      },
      {
        name: '小按钮',
        string: 'small'
      }
    ]
  })
  const disabledCodeInfo = reactive({
    tag: 's-button',
    attr: 'disabled',
    valueList: [{
      name: '默认按钮'
    }]
  })
  return {
    sizeCodeInfo,
    themeCodeInfo,
    disabledCodeInfo
  }
}
</script>

<style lang="scss" scoped>
button {
  margin-right: 10px;
}
</style>
