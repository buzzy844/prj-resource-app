<template>
  <ul>
    <Resource
      v-for="resource in this.resources"
      :key="resource.id"
      :title="resource.title"
      :description="resource.description"
      :link="resource.link"
      :id="resource.id"
      @delete-resource="deleteRsc"
    />
  </ul>
</template>

<script>
import Resource from './Resource.vue';

export default {
  props:['modelValue'],
  emits: ['del-res','update:modelValue'],
  components: { Resource },

  computed:{
    resources:{
      set(val){
        this.$emit('update:modelValue',val)
      },

      get(){
        return(this.modelValue)
      }
    }
  },

  methods: {
    deleteRsc(rscId) {
      this.resources = this.resources.filter((rsc) => rsc.id != rscId);
    },
  },
};
</script>

<style>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
