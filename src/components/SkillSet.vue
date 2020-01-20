<template>
  <table>
    <tbody>
    <tr :key="name" v-for="{name,confidence} in skills">
      <th v-text="name"/>
      <td :ref="name" v-text="`${confidence}%`"/>
    </tr>
    </tbody>
  </table>
</template>

<script>
  export default {
    name: 'skill-set',
    props: {
      skills: Array
    },
    mounted () {
      this.skills.forEach(({ name, confidence }) => {
        let pct = 0
        const interval = setInterval(() => {
          this.$refs[name][0].style.backgroundImage
            = `linear-gradient(0.25turn, rgba(200,255,200,0.75) ${pct}%, rgba(255,200,200,0.75) ${pct + 0.1}%)`
          if (pct++ >= confidence) clearInterval(interval)
        }, 10)
      })
    }
  }
</script>

<style lang="scss" scoped>
  table {
    width: 100%;

    tr {
      th {
        text-align: left;
      }

      td {
        text-shadow: 0 0 2px black;
        border-radius: 3px;
        padding-left: 0.5em;

        &:last-child {
          width: 100%;
        }
      }
    }
  }
</style>
