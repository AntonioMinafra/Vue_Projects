<template>
  <section>
    <base-card>
      <h2>Submitted Experiences</h2>
      <div>
        <base-button>Load Submitted Experiences</base-button>
      </div>
      <p v-if="isLoading">Loading...</p>
      <p v-else-if="!isLoading && (!results || results.length === 0)">No stored exeperiences found. Start adding some survey results first.</p>
      <ul v-else-if="!isLoading && results.length > 0" >
        <survey-result
          v-for="result in results"
          :key="result.id"
          :name="result.name"
          :rating="result.rating"
        ></survey-result>
      </ul>
    </base-card>
  </section>
</template>

<script>
import SurveyResult from './SurveyResult.vue';

export default {
  components: {
    SurveyResult,
  },
  data() {
    return {
      results: [],
      isLoading: false,
    }
  },
  methods: {
    loadExeperiences(){
      this.isLoading = true;
      fetch('https://vue-http-demo-e84e4-default-rtdb.europe-west1.firebasedatabase.app/surveys.json').then( (response) => {
        if (response.ok) {
          return response.json();
        }
      }
    ).then( (data) => {
      this.isLoading = false;
      const results = [];
      for (const id in data) {
        results.push({
          id: id,
          name: data[id].name,
          rating: data[id].rating
        });
      }
      this.results = results
    });
    },
  },
  mounted() {
    this.loadExeperiences();
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>