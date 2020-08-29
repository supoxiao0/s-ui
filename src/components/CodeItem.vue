<template>
<code class="code">
  <span v-for="(code,index) in codeInfo.valueList" :key="index" class="code-span">
    <span class="code-span-tag">&lt;</span>
    <span class="code-span-name">{{codeInfo.tag}}&nbsp;</span>
    <span v-for="(attr,idx) in code.attrList" :key="attr.string">
      <span class="code-span-attr">{{attr.attr}}</span>
      <span v-if="attr.string" class="code-span-string">"{{attr.string}}"</span>
      <span v-if="idx !== (code.attrList.length-1)">&nbsp;</span>
    </span>
    <span class="code-span-tag">&gt;</span>
    <span>{{code.name}}</span>
    <span class="code-span-tag">&lt;</span>
    <span class="code-span-name">/{{codeInfo.tag}}</span>
    <span class="code-span-tag">&gt;</span>
  </span>
  <span v-if="codeInfo.fragmentList" class="code-js">
    <span class="code-js-tag">&lt;script&gt;</span>
    <span class="code-js-keyword">export default {</span>
    <span class="code-js-setup">setup() {</span>
    <span v-for="(fragment,index) in codeInfo.fragmentList" :key="index" class="code-js-fragment">{{fragment.string}}</span>
    <span class="code-js-return">return {</span>
    <span v-for="(fragment,index) in codeInfo.fragmentList" :key="index" class="code-js-return-value">{{fragment.name}}</span>
    <span class="code-js-return">}</span>
    <span class="code-js-setup">}</span>
    <span class="code-js-keyword">}</span>
    <span class="code-js-tag">&lt;/script&gt;</span>
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
