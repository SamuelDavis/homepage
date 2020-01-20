<template>
  <div id="app">
    <main-nav :routes="mainNav"/>
    <div>
      <h3>Contact</h3>
      <contact :info="contact"/>
    </div>
  </div>
</template>

<script>
  import MainNav from './components/MainNav'
  import Contact from './components/Contact.vue'

  export default {
    name: 'app',
    components: {
      MainNav,
      Contact
    },
    data () {
      return {
        mainNav: [
          'Who',
          'What',
          'Where',
          'When',
          'Why',
        ],
        contact: {
          name: { text: 'Samuel Davis' },
          address: { text: 'Cornelius, NC', href: 'https://www.google.com/maps/place/Cornelius,+NC' },
          phone: { text: '802-745-0057', href: 'tel:802-745-0057' },
          email: { text: 'samueljakdavis@gmail.com', href: 'mailto:samueljakdavis@gmail.com' },
          website: { text: 'https://sdavis.online', href: 'https://sdavis.online' },
        }
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
