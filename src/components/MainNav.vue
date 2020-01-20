<template>
  <ul>
    <li :key="i" v-for="(text, i) in routes"><a @click="$emit('route', text)" href="#" v-text="text"/></li>
    <slot/>
  </ul>
</template>

<script>
  export default {
    name: 'main-nav',
    props: {
      routes: Array
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  $colorSyntax: rgb(166, 180, 194);
  $colorVars: rgb(120, 101, 133);
  $colorFunctions: rgb(254, 196, 109);

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;

    &, > li {
      &:before, &:after {
        white-space: nowrap;
        color: $colorSyntax;
      }
    }

    &:before {
      content: '$this';
      color: $colorVars;
    }

    &:after {
      content: ';';
    }

    li {
      &, > * {
        color: $colorFunctions;
      }

      a {
        text-decoration: none;

        &:hover {
          text-decoration: underline;
        }
      }

      > *:before {
        content: 'show'
      }

      &:before {
        content: '->';
      }

      &:after {
        content: '()';
      }
    }
  }
</style>
