<template>
    <ul>
      <li v-for="goal in goals" :key="goal">
        <slot :item="goal" :another-prop="'Some other prop value'"></slot>
      </li>
    </ul>
  </template>

  <script>
  export default {
    data() {
      return {
        goals: ['Finish the course', 'Learn Vue']
      };
    }
  };
  </script>
