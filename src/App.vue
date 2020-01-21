<template>
  <div id="app">
    <main-nav :routes="mainNav" v-on:route="changeRoute">
      <li><a href="https://notes.sdavis.online" target="_blank">Notes</a></li>
      <li><a href="https://github.com/SamuelDavis" target="_blank">GitHub</a></li>
      <li><a @click="print" href="#">PrintVersion</a></li>
    </main-nav>
    <section id="who" v-show="isVisible('who')">
      <h3>Info</h3>
      <contact :info="contact">
        <p>I have been a professional, end-to-end LAMP-stack web-developer since 2013. I spend my time coding small apps/tools/demos, reading about OPS, and listening to the dev community discuss app-architecture. You can find some of my more technical thoughts in <a href="https://notes.sdavis.online">my notebook</a>.</p>
      </contact>
    </section>
    <section id="what" v-show="isVisible('what')">
      <article :key="i" v-for="({label, skills},i) in skillSets">
        <h3 v-text="label"/>
        <skill-set v-bind:skills="skills"/>
      </article>
    </section>
    <section id="where" v-show="isVisible('where')">
      <h3>Experience</h3>
      <experience :key="i" v-bind="info" v-for="(info, i) in experiences"/>
    </section>
  </div>
</template>

<script>
  import MainNav from './components/MainNav'
  import Contact from './components/Contact.vue'
  import Experience from './components/Experience.vue'
  import SkillSet from './components/SkillSet.vue'

  export default {
    name: 'app',
    components: {
      MainNav,
      Contact,
      Experience,
      SkillSet
    },
    methods: {
      print () {
        window.print()
      },
      changeRoute (target) {
        this.route = target.toLowerCase()
      },
      isVisible (route) {
        return this.route === 'all' || this.route === route
      }
    },
    data () {
      return {
        route: 'all',
        mainNav: [
          'All',
          'Who',
          'What',
          'Where',
        ],
        skillSets: [
          {
            label: 'Languages',
            skills: [
              { name: 'HTML', confidence: 95 },
              { name: 'CSS', confidence: 75 },
              { name: 'PHP', confidence: 99 },
              { name: 'JS', confidence: 97 },
              { name: 'TypeScript', confidence: 75 },
              { name: 'SQL', confidence: 55 },
            ]
          },
          {
            label: 'Tools',
            skills: [
              { name: 'Unix', confidence: 85 },
              { name: 'Vim', confidence: 65 },
              { name: 'Docker', confidence: 83 },
              { name: 'AWS', confidence: 60 },
              { name: 'webpack', confidence: 62 },
            ]
          },
          {
            label: 'Frameworks',
            skills: [
              { name: 'Laravel', confidence: 80 },
              { name: 'Vue', confidence: 77 },
              { name: 'Vuex', confidence: 70 },
              { name: 'Bootstrap', confidence: 70 },
              { name: 'WordPress', confidence: 70 },
              { name: 'CraftCMS', confidence: 60 }
            ]
          }
        ],
        contact: {
          name: { text: 'Samuel Davis' },
          address: { text: 'Cornelius, NC', href: 'https://www.google.com/maps/place/Cornelius,+NC' },
          phone: { text: '802-745-0057', href: 'tel:802-745-0057' },
          email: { text: 'samueljakdavis@gmail.com', href: 'mailto:samueljakdavis@gmail.com' },
          website: { text: 'https://sdavis.online', href: 'https://sdavis.online' },
        },
        experiences: [
          {
            name: 'AlterImaging',
            location: 'Charlotte, NC',
            from: new Date('4/18/2019'),
            to: undefined,
            role: 'Jr. Software Developer',
            comments: 'I manage hosting, trouble-shoot legacy PHP applications, and maintain WordPress/CraftCMS sites here. This consists mostly of mucking with cPanel\'s Web Hosting Manager, SSHing into servers and reading logs, lightweight UI apps/styling for marketing sites, and project-management back-and-forth.'
          },
          {
            name: 'Gold Silver LLC',
            location: 'Burlington, VT',
            from: new Date('3/1/2017'),
            to: new Date('6/21/2018'),
            role: 'Software Engineer',
            comments: 'I was the lead-(only-)developer and architect for both the front- and back-end of a precious-metals e-commerce/trading platform. I partially implemented a microservice pattern to build a very robust frontend. I spent incredible amounts of time in meetings with partner-companies trying to spec the backend. I learned a huge amount and was moderately successful.'
          },
          {
            name: 'Daft Labs',
            location: 'Burlington, VT',
            from: new Date('6/1/2014'),
            to: new Date('2/1/2017'),
            role: 'Software Engineer',
            comments: 'This was all agency work for exciting and often well-funded start-ups. This was where I learned the difference between code and clean code, and how architecture is the challenge of a real developer. Mostly I was designing and building REST APIs, but I was often the on-call guy to help any team or client; I was often put to OPS work and became familiar with AWS as well as concepts like containerization through Chef and Docker.'
          },
          {
            name: 'BurlingtonBytes',
            location: 'Burlington, VT',
            from: new Date('10/1/2013'),
            to: new Date('6/1/2014'),
            role: 'Software Engineer',
            comments: 'This job had two parts; agency work as a WordPress shop and maintaining a legacy, plain-old-PHP firearms-manufacturing back office application. Building plugins for WordPress was unremarkable. The manufacturing back office app was a real rat\'s nest of PHP, jQuery, and SQL which taught me the virtues of functional programming - building isolated apps which interfaced with the legacy app without disturbing it.'
          },
          {
            name: 'Bluehouse Group',
            location: 'Richmond, VT',
            from: new Date('2/1/2013'),
            to: new Date('9/1/2013'),
            role: 'Software Engineer',
            comments: 'This was mostly peculiar apps for start-ups; QuizBean.com was where most of the work went, but there were also small apps to automate social-media work, or complicated templating for brochure sites.'
          },
          {
            name: 'BurlingtonBytes',
            location: 'Burlington, VT',
            from: new Date('10/1/2012'),
            to: new Date('12/1/2013'),
            role: 'Software Engineer Intern',
            comments: 'This was just a continuation of my college intern work: WordPress marketing sites, or WordPress-plugin applications. The most remarkable accomplishment during this time was a web scraper which automatically generated pages from re-formatted content.'
          },
          {
            name: 'Champlain College',
            location: 'Burlington, VT',
            from: new Date('10/1/2012'),
            to: new Date('2/1/2013'),
            role: 'Software Engineer Intern',
            comments: 'This was pretty generic intern work: prototyping a custom social media application internal to the college and a time-keeping SPA before they were cool.'
          }
        ]
      }
    }
  }
</script>

<style lang="scss">
  $lineHeight: 16px;
  $colorText: rgb(166, 180, 194);
  $colorBg: rgb(42, 42, 42);

  @media print {
    section {
      display: block !important;

      &#what {
        display: flex !important;
      }
    }
  }

  * {
    color: $colorText;
    font-size: $lineHeight;
    line-height: $lineHeight;
  }

  html {
    background-color: $colorBg;
    font-family: monospace;
  }

  #what {
    display: flex;
    flex-wrap: wrap;

    > * {
      flex: 1;
    }
  }
</style>
