<template>
<Switch v-model:value="active" :disabled="true" :width="60" />
</template>

<script lang="ts">
import Switch from '../libs/Switch.vue'
import {
  ref
} from 'vue'
export default {
  components: {
    Switch
  },
  setup() {
    const active = ref(true)
    return {
      active
    }
  }
}
</script>
