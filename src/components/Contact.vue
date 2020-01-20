<template>
  <address>
    <table>
      <tbody>
      <tr :key="label" v-for="({text, href}, label) in info">
        <th v-text="label"/>
        <td>
          <a :href="href" target="_blank" v-if="href" v-text="text"/>
          <h1 v-else v-text="text"/>
        </td>
      </tr>
      </tbody>
    </table>
    <slot/>
  </address>
</template>

<script>
  export default {
    name: 'contact',
    props: {
      info: Object
    }
  }
</script>

<style lang="scss" scoped>
  address {
    display: flex;
    flex-wrap: wrap;

    > * {
      margin-top: 0;
      flex: 1;
    }

    h1 {
      margin: 0;
    }

    table {
      margin-bottom: 1em;

      th {
        text-align: left;
        padding-right: 2em;
        text-transform: capitalize;
      }
    }
  }
</style>
