<template>
  <article>
    <ul>
      <li><b v-text="name"/></li>
      <li v-text="role"/>
      <li class="dates">
        <span :key="i" v-for="(date, i) in [from, to]" v-if="date" v-text="formatDate(date)"/>
      </li>
      <li>
        <a :href="formatLocation(location)" target="_blank" v-text="location"/>
      </li>
    </ul>
    <p v-text="comments"/>
  </article>
</template>

<script>
  export default {
    name: 'experience',
    props: {
      name: String,
      role: String,
      from: Date,
      to: Date,
      location: String,
      comments: String
    },
    methods: {
      formatDate (date) {
        return [date.getMonth() + 1, date.getDate(), date.getFullYear()].join('/')
      },
      formatLocation (location) {
        return `https://www.google.com/maps/place/${location.replace(/\s+/, '+')}`
      }
    }
  }
</script>

<style lang="scss" scoped>
  article {
    @media print {
      break-inside: avoid;
    }
    ul {
      list-style-type: none;

      li {
        display: inline-block;

        &:first-child {
          font-weight: bold;
        }

        &.dates {
          *:not(:last-child):after {
            content: '-';
            margin: 0 0.25em;
          }
        }

        &:not(:last-child):after {
          content: '|';
          margin: 0 0.25em;
        }
      }
    }
  }
</style>
