<template>
  <div id="app">
    <main-nav :routes="mainNav"/>
  </div>
</template>

<script>
  import MainNav from './components/MainNav'

  export default {
    name: 'app',
    components: {
      MainNav
    },
    data () {
      return {
        mainNav: [
          'Who',
          'What',
          'Where',
          'When',
          'Why',
        ]
      }
    }
  }
</script>

<style lang="scss">
  $colorText: rgb(166, 180, 194);
  $colorBg: rgb(42, 42, 42);

  * {
    color: $colorText;
  }

  html {
    background-color: $colorBg;
    font-family: "Source Code Pro", "SF Mono", Monaco, Inconsolata, "Fira Mono", "Droid Sans Mono", monospace;
  }
</style>
