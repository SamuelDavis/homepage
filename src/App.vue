<template>
    <div id="app">
        <h1 id="title">Samuel Davis' Resume</h1>
        <main-nav :routes="mainNav" v-on:route="changeRoute">
            <li><a href="https://notes.sdavis.online" target="_blank">Notes</a></li>
            <li><a href="https://github.com/SamuelDavis" target="_blank">GitHub</a></li>
            <li><a @click="print" href="#">PrintVersion</a></li>
        </main-nav>
        <section id="who" v-show="isVisible('who')">
            <h3>Info</h3>
            <contact :info="contact">
                <p>I have been a professional, end-to-end LAMP-stack web-developer since 2013. I spend my time coding small apps/tools/demos, reading about OPS, and listening to the dev community discuss app-architecture.<span id="notebook-link">You can find some of my more technical thoughts in <a href="https://notes.sdavis.online" target="_blank">my notebook</a>.</span></p>
            </contact>
        </section>
        <section id="what" v-show="isVisible('what')">
            <article :key="i" v-for="({label, skills, notice = undefined},i) in skillLevels">
                <h3 v-text="label"/>
                <skill-level v-bind="{skills, notice}"/>
            </article>
            <skill-description :key="i" v-bind="skill" v-for="(skill, i) in skillDescriptions"/>
        </section>
        <section id="where" v-show="isVisible('where')">
            <h3>Experience</h3>
            <experience :key="i" v-bind="info" v-for="(info, i) in experiences"/>
        </section>
    </div>
</template>

<script>
  import MainNav from './components/MainNav'
  import Contact from './components/Contact'
  import Experience from './components/Experience'
  import SkillLevel from './components/SkillLevel'
  import SkillDescription from './components/SkillDescription'

  export default {
    name: 'app',
    components: {
      MainNav,
      Contact,
      Experience,
      SkillLevel,
      SkillDescription
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
        skillLevels: [
          {
            label: 'Languages',
            skills: [
              { name: 'HTML', confidence: 95 },
              { name: 'CSS', confidence: 75 },
              { name: 'PHP', confidence: 99 },
              { name: 'JS', confidence: 97 },
              { name: 'SQL', confidence: 55 },
            ],
            notice: '*Also TypeScript & SCSS.'
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
              { name: 'Laravel', confidence: 90 },
              { name: 'Vue', confidence: 77 },
              { name: 'Vuex', confidence: 70 },
              { name: 'Bootstrap', confidence: 70 },
              { name: 'WordPress', confidence: 67 },
              { name: 'CraftCMS', confidence: 60 }
            ]
          }
        ],
        skillDescriptions: [
          { label: 'API Integration', description: 'Modeling data, the transporting of data, and the execution of use cases should (normally) be independent of each other.' },
          { label: 'Domain Driven Design', description: 'Even when building a monolith, it is useful to think of your application as microservices which are composed.' },
          { label: 'Front-end Development', description: 'I am familiar with developing mobile-friendly/mobile-first applications with tools like CSS Flex and CSS Grid.' },
          { label: 'DevOps', description: 'I use Docker every day; I understand that containerized applications are easier to develop, deploy, and debug.' },
          { label: 'MVC', description: 'If the application is too large or complex, it is better to create specialized models which the controllers can transform.' },
          { label: 'Dev Lifecycle', description: 'Rapid, MVP, something-better-than-nothing: Develop as many parts of application as simultaneously as possible.' },
          { label: 'Data Processing', description: 'In a PHP context; if there is a lot of data to process, find a way to chunk that data and then boot multiple processes to process each chunk - let the OS handle threading for you.' },
          { label: 'Optimization', description: 'Regularly-accessed data should be cached in-memory: this can be in a dedicated service like Redis, or per process; use meaningful indexing in your database and your application.' }
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
            role: 'Lead Software Developer',
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
    $colorText: rgb(166, 180, 194);
    $colorBg: rgb(42, 42, 42);

    * {
        font-family: Arial, sans-serif;
    }

    @media print {
        #title {
            display: block !important;
            font-size: 150%;
            margin-bottom: 1.5em;
        }

        #who h3 {
            display: none;
        }

        #notebook-link {
            display: none;
        }

        section {
            display: block !important;
            break-inside: avoid;

            &#what {
                display: flex !important;
            }
        }

        a {
            text-decoration: none;
        }
    }

    * {
        color: $colorText;
    }

    html {
        background-color: $colorBg;
    }

    article {
        margin-bottom: 1em;
    }

    #title {
        display: none;
    }

    #what {
        display: flex;
        flex-wrap: wrap;
        align-items: start;
        justify-content: space-evenly;

        > * {
            flex: 0 1 30%;

            @media (max-width: 415px) {
                flex-basis: 100%;
            }
        }
    }
</style>
