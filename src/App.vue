<template>
  <div id="app">
    <main-nav :routes="mainNav"/>
    <div>
      <section>
        <h3>Contact</h3>
        <contact :info="contact"/>
      </section>
      <section :key="i" v-for="({label, skills},i) in skillSets">
        <h3 v-text="label"/>
        <skill-set v-bind:skills="skills"/>
      </section>
      <section>
        <h3>Experience</h3>
        <experience :key="i" v-bind="info" v-for="(info, i) in experiences"/>
      </section>
    </div>
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
    data () {
      return {
        mainNav: [
          'Who',
          'What',
          'Where',
          'When',
          'Why',
        ],
        skillSets: [
          {
            label: 'Languages',
            skills: [
              { name: 'HTML', confidence: 95 },
              { name: 'CSS', confidence: 75 },
              { name: 'PHP', confidence: 99 },
              { name: 'JS', confidence: 97 },
              { name: 'SQL', confidence: 55 },
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
            comments: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris aliquam sollicitudin consequat. Etiam euismod nisl eu convallis mollis. Ut vitae ipsum vitae purus bibendum laoreet ac eu eros. Quisque laoreet quam eget turpis vulputate posuere. Aliquam varius bibendum cursus. Quisque et nisl rhoncus, blandit enim vestibulum, vulputate enim. Curabitur fermentum.'
          },
          {
            name: 'Gold Silver LLC',
            location: 'Burlington, VT',
            from: new Date('3/1/2017'),
            to: new Date('6/21/2018'),
            role: 'Software Engineer',
            comments: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris aliquam sollicitudin consequat. Etiam euismod nisl eu convallis mollis. Ut vitae ipsum vitae purus bibendum laoreet ac eu eros. Quisque laoreet quam eget turpis vulputate posuere. Aliquam varius bibendum cursus. Quisque et nisl rhoncus, blandit enim vestibulum, vulputate enim. Curabitur fermentum.'
          },
          {
            name: 'Daft Labs',
            location: 'Burlington, VT',
            from: new Date('6/1/2014'),
            to: new Date('2/1/2017'),
            role: 'Software Engineer',
            comments: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris aliquam sollicitudin consequat. Etiam euismod nisl eu convallis mollis. Ut vitae ipsum vitae purus bibendum laoreet ac eu eros. Quisque laoreet quam eget turpis vulputate posuere. Aliquam varius bibendum cursus. Quisque et nisl rhoncus, blandit enim vestibulum, vulputate enim. Curabitur fermentum.'
          },
          {
            name: 'BurlingtonBytes',
            location: 'Burlington, VT',
            from: new Date('10/1/2013'),
            to: new Date('6/1/2014'),
            role: 'Software Engineer',
            comments: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris aliquam sollicitudin consequat. Etiam euismod nisl eu convallis mollis. Ut vitae ipsum vitae purus bibendum laoreet ac eu eros. Quisque laoreet quam eget turpis vulputate posuere. Aliquam varius bibendum cursus. Quisque et nisl rhoncus, blandit enim vestibulum, vulputate enim. Curabitur fermentum.'
          },
          {
            name: 'Bluehouse Group',
            location: 'Richmond, VT',
            from: new Date('2/1/2013'),
            to: new Date('9/1/2013'),
            role: 'Software Engineer',
            comments: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris aliquam sollicitudin consequat. Etiam euismod nisl eu convallis mollis. Ut vitae ipsum vitae purus bibendum laoreet ac eu eros. Quisque laoreet quam eget turpis vulputate posuere. Aliquam varius bibendum cursus. Quisque et nisl rhoncus, blandit enim vestibulum, vulputate enim. Curabitur fermentum.'
          },
          {
            name: 'BurlingtonBytes',
            location: 'Burlington, VT',
            from: new Date('10/1/2012'),
            to: new Date('12/1/2013'),
            role: 'Software Engineer Intern',
            comments: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris aliquam sollicitudin consequat. Etiam euismod nisl eu convallis mollis. Ut vitae ipsum vitae purus bibendum laoreet ac eu eros. Quisque laoreet quam eget turpis vulputate posuere. Aliquam varius bibendum cursus. Quisque et nisl rhoncus, blandit enim vestibulum, vulputate enim. Curabitur fermentum.'
          },
          {
            name: 'Champlain College',
            location: 'Burlington, VT',
            from: new Date('10/1/2012'),
            to: new Date('2/1/2013'),
            role: 'Software Engineer Intern',
            comments: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris aliquam sollicitudin consequat. Etiam euismod nisl eu convallis mollis. Ut vitae ipsum vitae purus bibendum laoreet ac eu eros. Quisque laoreet quam eget turpis vulputate posuere. Aliquam varius bibendum cursus. Quisque et nisl rhoncus, blandit enim vestibulum, vulputate enim. Curabitur fermentum.'
          },
          {
            name: 'Engineering Ventures',
            location: 'Burlington, VT',
            from: new Date('4/1/2012'),
            to: new Date('4/28/2012'),
            role: 'Storage Archivist',
            comments: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris aliquam sollicitudin consequat. Etiam euismod nisl eu convallis mollis. Ut vitae ipsum vitae purus bibendum laoreet ac eu eros. Quisque laoreet quam eget turpis vulputate posuere. Aliquam varius bibendum cursus. Quisque et nisl rhoncus, blandit enim vestibulum, vulputate enim. Curabitur fermentum.'
          },
          {
            name: 'Regional Grocery and Inventory Service',
            location: 'Burlington, VT',
            from: new Date('12/1/2011'),
            to: new Date('10/1/2012'),
            role: 'Inventory Taker',
            comments: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris aliquam sollicitudin consequat. Etiam euismod nisl eu convallis mollis. Ut vitae ipsum vitae purus bibendum laoreet ac eu eros. Quisque laoreet quam eget turpis vulputate posuere. Aliquam varius bibendum cursus. Quisque et nisl rhoncus, blandit enim vestibulum, vulputate enim. Curabitur fermentum.'
          },
          {
            name: 'JPMorgan Chase',
            location: 'Williston, VT',
            from: new Date('6/1/2010'),
            to: new Date('9/1/2010'),
            role: 'Data Entry',
            comments: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris aliquam sollicitudin consequat. Etiam euismod nisl eu convallis mollis. Ut vitae ipsum vitae purus bibendum laoreet ac eu eros. Quisque laoreet quam eget turpis vulputate posuere. Aliquam varius bibendum cursus. Quisque et nisl rhoncus, blandit enim vestibulum, vulputate enim. Curabitur fermentum.'
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

  * {
    color: $colorText;
    font-size: $lineHeight;
    line-height: $lineHeight;
  }

  html {
    background-color: $colorBg;
    font-family: monospace;
  }

  #app > div {
    display: flex;
    flex-wrap: wrap;

    section {
      flex: 1;
      min-width: fit-content;
    }
  }
</style>
