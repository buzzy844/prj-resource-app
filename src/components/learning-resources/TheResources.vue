<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resources')" :mode="storedResButtonMode">Stored Resources</base-button>
    <base-button @click="setSelectedTab('add-resources')" :mode="addResButtonMode">Add Resources</base-button>
  </base-card>
  <component :is="selectedTab" v-model="storedResources"></component>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResources from './AddResource.vue';

export default {
  components: {
    StoredResources,
    AddResources,
  },

  provide() {
    return {
      goToResources: () => {
        this.selectedTab = 'stored-resources';
      },
    };
  },

  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js docs',
          link: 'https://vuejs.org',
        },
        { id: 'google', title: 'Google', description: 'Learning to google code stuff', link: 'https://google.com' },
      ],
    };
  },

  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },

    addResButtonMode() {
      return this.selectedTab === 'add-resources' ? null : 'flat';
    },
  },

  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
  },
};
</script>
