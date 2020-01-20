<template>
  <address>
    <table>
      <tbody>
      <tr :key="label" v-for="({text, href}, label) in info">
        <th v-text="label"/>
        <td>
          <a :href="href" target="_blank" v-if="href" v-text="text"/>
          <h3 v-else v-text="text"/>
        </td>
      </tr>
      </tbody>
    </table>
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
    h3 {
      margin: 0;
    }

    table {
      th {
        text-align: left;
        padding-right: 2em;
        text-transform: capitalize;
      }
    }
  }
</style>
