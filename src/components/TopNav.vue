<template>
<div class="topnav">
  <div class="red" @click="toggleAsideVisble"></div>
  <div class="logo">我是logo</div>
  <ul class="menu">
    <li>菜单一</li>
    <li>菜单二</li>
  </ul>
</div>
</template>

<script lang="ts">
import {
  inject,
  Ref
} from 'vue'
export default {
  setup(props) {
    let asideVisble = inject < Ref < boolean >> ('asideVisble')
    const toggleAsideVisble = () => {
      asideVisble.value = !asideVisble.value
    }
    return {
      asideVisble,
      toggleAsideVisble
    }
  }
}
</script>

<style lang="scss" scoped>
.topnav {
  background: pink;
  display: flex;
  padding: 16px;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 10;

  >.logo {
    max-width: 6em;
    margin-right: auto;
  }

  >.red {
    width: 30px;
    height: 30px;
    background: red;
    display: none;
  }

  >.menu {
    display: flex;
    white-space: nowrap;
    flex-wrap: nowrap;

    >li {
      margin: 0 1em;
    }
  }

  @media (max-width: 700px) {
    >.menu {
      display: none;
    }

    >.red {
      display: block;
    }

    >.logo {
      margin: 0 auto;
    }
  }
}
</style>
