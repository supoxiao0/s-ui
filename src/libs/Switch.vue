<template>
<button class="s-switch" :class="switchClass" :style="colorStyle" @click="toggle">
  <span class="s-switch-button"></span>
</button>
</template>

<script>
import {
  computed
} from 'vue'
export default {
  props: {
    value: {
      type: Boolean,
      default: false
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  setup(props, context) {
    const defaultActiveBgColor = '#409eff'
    const defaultInActiveBgColor = '#dcdfe6'
    const toggle = () => {
      if (!props.disabled) {
        context.emit('update:value', !props.value)
        context.emit('change', !props.value)
      }
    }
    const switchClass = computed(() => {
      return {
        [`s-switch-active`]: props.value,
        [`s-switch-disabled`]: props.disabled
      }
    })
    const colorStyle = computed(() => {
      if (props.value) {
        return {
          backgroundColor: context.attrs['active-color'] ? context.attrs['active-color'] : defaultActiveBgColor
        }
      } else {
        return {
          backgroundColor: context.attrs['inactive-color'] ? context.attrs['inactive-color'] : defaultInActiveBgColor
        }
      }
    })
    return {
      toggle,
      switchClass,
      colorStyle
    }
  }
}
</script>

<style lang="scss" scoped>
$w: 40px;
$w2: 16px;

.s-switch {
  position: relative;
  width: $w;
  height: $w/2;
  border-radius: $w/4;
  // background-color: #dcdfe6;
  cursor: pointer;
  border: none;

  >.s-switch-button {
    width: $w2;
    height: $w2;
    border-radius: 100%;
    background-color: #fff;
    position: absolute;
    top: 2px;
    left: 2px;
    transition: left .3s;
  }

  &.s-switch-active {
    // background-color: #409eff;

    >.s-switch-button {
      left: calc(100% - #{$w2} - 2px);
    }
  }

  &:focus {
    outline: none;
  }

  &.s-switch-disabled {
    opacity: .6;
    cursor: default;
  }
}
</style>
