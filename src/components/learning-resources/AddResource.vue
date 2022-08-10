<template>
  <base-card>
    <form>
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" v-model="this.enteredResource.title" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea id="description" name="description" rows="3" v-model="this.enteredResource.description"></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" name="link" type="url" v-model="this.enteredResource.link" />
      </div>
      <base-button type="submit" @click.prevent @click="submitRsc">Submit</base-button>
    </form>
  </base-card>
</template>

<script>
export default {
  emits:['update:modelValue'],
  props:['modelValue'],
  inject:['goToResources'],

  data() {
    return {
      enteredResource: {
        id: Math.random(),
      },
    };
  },

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
    submitRsc() {
      const rscCopy = {...this.enteredResource};
      this.resources.push(rscCopy);
      this.goToResources();
    },
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
