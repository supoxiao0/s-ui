<template>
<button class="s-button" :class="buttonClass">
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
    }
  },
  setup(props, context) {
    const {
      size,
      theme
    } = props
    const buttonClass = computed(() => {
      return `s-button-${size} s-button-${theme}`
    })
    return {
      buttonClass
    }
  }
}
</script>

<style lang="scss">
  
</style>
