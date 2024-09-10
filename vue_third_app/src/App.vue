<template>
  <div>
    <the-header></the-header>
    <button @click="setselectedComponent('active-goals')">Active goals</button>
    <button @click="setselectedComponent('menage-goals')">Menage Goals</button>
<!--     <active-goals v-if="selectedComponent === 'active-goals'"></active-goals>
    <menage-goals v-if="selectedComponent === 'menage-goals'"></menage-goals> -->
    <!-- componente dinamico fatto sopra con molto codice e qui sotto con l'elemento component quindi meno sintassi-->
     <keep-alive>
       <component :is="selectedComponent"></component>
     </keep-alive>
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
/* import BadgeList from './components/BadgeList.vue';
import UserInfo from './components/UserInfo.vue';
import CourseGoals from './components/CourseGoals.vue'; */
import MenageGoals from './components/MenageGoals.vue';
import ActiveGoals from './components/ActiveGoals.vue';

export default {
  components: {
    'the-header': TheHeader,
/*     'badge-list': BadgeList,
    'user-info': UserInfo,
    'course-goals': CourseGoals, */
    'menage-goals': MenageGoals,
    'active-goals': ActiveGoals,
  },
  data() {
    return {
      selectedComponent: 'active-goals',
      activeUser: {
        name: 'Maximilian Schwarzmüller',
        description: 'Site owner and admin',
        role: 'admin',
      },
    };
  },
  methods: {
    setselectedComponent(cmp) {
      this.selectedComponent = cmp
    },
  },
};
</script>

<style scoped>
html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>
