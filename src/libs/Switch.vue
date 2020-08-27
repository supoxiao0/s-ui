<template>
<button class="s-switch" :class="{'active': value, 'is-disabled': disabled}" @click="toggle">
  <span class="s-switch-button"></span>
</button>
</template>

<script>
export default {
  props: {
    value: {
      type: Boolean,
      default: false
    },
    disabled: {
      type: Boolean,
      default: false
    },
    width: {
      type: Number,
      default: 40
    }
  },
  setup(props, context) {
    const toggle = () => {
      if (!props.disabled) {
        context.emit('update:value', !props.value)
        context.emit('change', !props.value)
      }
    }
    return {
      toggle
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
  background-color: #dcdfe6;
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

  &.active {
    background-color: #409eff;

    >.s-switch-button {
      left: calc(100% - #{$w2} - 2px);
    }
  }

  &:focus {
    outline: none;
  }

  &.is-disabled {
    opacity: .6;
  }
}
</style>
