<template>
<button class="s-button" :disabled="disabled" :class="buttonClass">
  <slot />
</button>
</template>

<script lang="ts">
import {
  computed
} from 'vue'
export default {
  props: {
    size: {
      type: String,
      default: 'medium'
    },
    theme: {
      type: String,
      default: 'default'
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  setup(props, context) {
    const {
      size,
      theme,
      disabled
    } = props
    const buttonClass = computed(() => {
      return {
        [`s-button-size-${size}`]: theme,
        [`s-button-theme-${theme}`]: size,
        [`s-button-disabled`]: disabled
      }
    })
    return {
      buttonClass
    }
  }
}
</script>

<style lang="scss">
.s-button {
  display: inline-block;
  white-space: nowrap;
  outline: none;
  text-align: center;
  line-height: 1;
  cursor: pointer;
  transition: .1s;
  border: 1px solid #dcdfe6;
  font-size: 14px;
  border-radius: 4px;

  &.s-button-theme-default {
    color: #fff;
    background-color: #409eff;
    border-color: #409eff;
  }

  &.s-button-theme-success {
    color: #fff;
    background-color: #67c23a;
    border-color: #67c23a;
  }

  &.s-button-theme-warning {
    color: #fff;
    background-color: #e6a23c;
    border-color: #e6a23c;
  }

  &.s-button-theme-danger {
    color: #fff;
    background-color: #f56c6c;
    border-color: #f56c6c;
  }

  &.s-button-theme-plain {
    background-color: #fff;
  }

  &.s-button-size-big {
    padding: 12px 20px;
  }

  &.s-button-size-medium {
    padding: 9px 15px;
    font-size: 12px;
    border-radius: 3px;
  }

  &.s-button-size-small {
    padding: 7px 15px;
    font-size: 12px;
    border-radius: 3px;
  }

  &.s-button-disabled {
    opacity: .6;
    cursor: default;
  }
}
</style>
