<template>
<div class="switch-demo">
  <h1 class="demo-title">Switch开关</h1>
  <div class="demo-ctn">
    <h2>基础用法</h2>
    <div class="demo-list">
      <div class="source">
        <Switch v-model:value="active" active-color="#13ce66" inactive-color="#ff4949" />
      </div>
      <div v-show="basicCodeShow" class="code-ctn">
        <p class="desc">使用<code>value</code>，一个<code>Boolean</code>类型的值来设置Switch的开关状态。使用<code>active-color</code>属性与<code>inactive-color</code>属性来设置开关的背景色
        </p>
        <CodeItem :codeInfo="basicCodeInfo" />
      </div>
      <div class="code-control" @click="toggle(1)">
        <span v-if="basicCodeShow">隐藏代码</span>
        <span v-else>显示代码</span>
      </div>
    </div>
  </div>
  <div class="demo-ctn">
    <h2>禁用状态</h2>
    <div class="demo-list">
      <div class="source">
        <Switch v-model:value="active1" disabled />
        <Switch v-model:value="active2" disabled />
      </div>
      <div v-show="disabledCodeShow" class="code-ctn">
        <p class="desc">使用<code>disabled</code>，接受一个<code>Boolean</code>，设置<code>true</code>即可禁用。
        </p>
        <CodeItem :codeInfo="disabledCodeInfo" />
      </div>
      <div class="code-control" @click="toggle(2)">
        <span v-if="disabledCodeShow">隐藏代码</span>
        <span v-else>显示代码</span>
      </div>
    </div>
  </div>
</div>
</template>

<script lang="ts">
import {
  reactive
} from 'vue'
import Switch from '../libs/Switch.vue'
import CodeItem from './CodeItem.vue'
import {
  ref
} from 'vue'
export default {
  components: {
    Switch,
    CodeItem
  },
  setup() {
    const active = ref(true)
    const active1 = ref(true)
    const active2 = ref(false)
    const {
      basicCodeShow,
      disabledCodeShow,
      toggle
    } = handleCodeShow()
    const {
      basicCodeInfo,
      disabledCodeInfo
    } = initData()
    return {
      active,
      active1,
      active2,
      basicCodeShow,
      disabledCodeShow,
      basicCodeInfo,
      disabledCodeInfo,
      toggle
    }
  }
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

function initData() {
  const basicCodeInfo = reactive({
    tag: 's-switch',
    valueList: [{
      name: '',
      attrList: [{
          attr: ':value=',
          string: 'active'
        },
        {
          attr: 'active-color=',
          string: '#13ce66'
        },
        {
          attr: 'inactive-color=',
          string: '#ff4949'
        }
      ]
    }],
    fragmentList: [{
      name: 'active',
      string: 'const active = ref(true)'
    }]
  })
  const disabledCodeInfo = reactive({
    tag: 's-switch',
    valueList: [{
      name: '',
      attrList: [{
        attr: ':value=',
        string: 'active1'
      }, {
        attr: 'disabled'
      }]
    }, {
      name: '',
      attrList: [{
        attr: ':value=',
        string: 'active2'
      }, {
        attr: 'disabled'
      }]
    }],
    fragmentList: [{
      name: 'active1',
      string: 'const active1 = ref(true)'
    }, {
      name: 'active2',
      string: 'const active2 = ref(false)'
    }]
  })
  return {
    basicCodeInfo,
    disabledCodeInfo
  }
}
</script>

<style lang="scss" scoped>
.source {
  >button {
    margin-right: 10px;
  }
}
</style>
