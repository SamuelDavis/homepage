<template>
    <table>
        <tbody>
        <tr :key="name" v-for="{name,confidence} in skills">
            <th v-text="name"/>
            <td :ref="name" v-text="`${confidence}%`"/>
        </tr>
        <tr v-if="notice">
            <td colspan="2">
                <small v-text="notice"/>
            </td>
        </tr>
        </tbody>
    </table>
</template>

<script>
  export default {
    name: 'skill-level',
    props: {
      skills: Array,
      notice: String,
    },
    mounted () {
      this.skills.forEach(({ name, confidence }) => {
        let pct = 0
        const interval = setInterval(() => {
          this.$refs[name][0].style.backgroundImage
            = `linear-gradient(0.25turn, rgba(200,255,200,0.75) ${pct}%, rgba(169,169,169,0.75) ${pct + 0.1}%)`
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
                @media print {
                    text-shadow: none;
                }

                color: black;
                border-radius: 3px;
                padding-left: 0.5em;

                &:last-child {
                    width: 100%;
                }
            }
        }
    }
</style>
