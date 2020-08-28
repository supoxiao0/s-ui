<template>
<code class="code">
  <span v-for="code in codeInfo.valueList" :key="code.string" class="code-span">
    <span class="code-span-tag">&lt;</span>
    <span class="code-span-name">{{codeInfo.tag}}&nbsp;</span>
    <span class="code-span-attr">{{codeInfo.attr}}<i v-if="code.string">=</i></span>
    <span v-if="code.string" class="code-span-string">"{{code.string}}"</span>
    <span class="code-span-tag">&gt;</span>
    <span>{{code.name}}</span>
    <span class="code-span-tag">&lt;</span>
    <span class="code-span-name">/{{codeInfo.tag}}</span>
    <span class="code-span-tag">&gt;</span>
  </span>
</code>
</template>

<script lang="ts">
export default {
  props: {
    codeInfo: {
      type: Object,
      default () {
        return {}
      }
    }
  }
}
</script>
