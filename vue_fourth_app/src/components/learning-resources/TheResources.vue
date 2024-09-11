<template>
  <base-card>
  <base-button @click="setSelectedTab('stored-resources')" :mode="storeResButton">Stored Resources</base-button>
  <base-button @click="setSelectedTab('add-resources')" :mode="addResButton">Add Resource</base-button>
</base-card>
<keep-alive>
  <component :is="selectedTab"></component>
</keep-alive>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue'
import BaseCard from '../UI/BaseCard.vue'
import AddResources from './AddResources.vue';
import StoredResources from './StoredResources.vue'


export default {
  components: { BaseCard, BaseButton, StoredResources, AddResources },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
      { id: 'official-guide', title: 'Official Guide', description: 'The official Vue.js documentation', link: 'https://vuejs.org' },
      { id: 'google', title: 'Google', description: 'Learn to google...', link: 'https://google.com' }
      ]
    }
  },
  computed: {
    storeResButton(){
      return this.selectedTab === 'stored-resources' ? null : 'flat'
    },
    addResButton(){
      return this.selectedTab === 'add-resources' ? null : 'flat'
    }
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      deleteResource: this.removeResource
    };
  },
  methods: {
    setSelectedTab(tab){
      this.selectedTab = tab;
    },
    addResource(title, description, link) {
      const newResources = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: link
      };
      this.storedResources.unshift(newResources);
      this.selectedTab = 'stored-resources';
    },
    removeResource(resId){
      const resIndex = this.storedResources.findIndex(res => res.id === resId);
      this.storedResources.splice(resIndex, 1);
    }
  },

}
</script>
