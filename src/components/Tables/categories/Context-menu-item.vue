<template>
  <li class="context-menu-item">
    <slot></slot>
  </li>
</template>
<script>
  export default {
    name: 'ContextMenuItem',
    props: {
      icon: ''
    }
  }
</script>
<style scoped>
  html, body, #app {
    margin: 0;
    width: 100%;
    height: 100%;
    display: flex;
    text-align: center;
    align-items: center;
    justify-content: center;
    background-color: #343338;
    font-family: Roboto, Tahoma, sans-serif;
  }

  .logo {
    height: 100px;
  }

  .instructions {
    color: white;
    display: block;
    font-size: 25px;
  }

  #context-menu {
    top: 0;
    left: 0;
    margin: 0;
    padding: 0;
    display: none;
    list-style: none;
    position: absolute;
    z-index: 2147483647;
    background-color: white;
    border: 1px solid #ebebeb;
    border-bottom-width: 0px;
  }

  #context-menu.active {
    display: block;
  }

  .context-menu-icon {
    top: 1px;
    position: relative;
    margin-right: 10px;
  }

  .context-menu-item {
    display: flex;
    cursor: pointer;
    padding: 8px 15px;
    align-items: center;
    border-bottom: 1px solid #ebebeb;
  }

  .context-menu-item:hover {
    background-color: #ebebeb;
  }
</style>
