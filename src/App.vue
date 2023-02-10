<template>
  <div id="app">
    <input v-model="searchQuery">
    <div v-for="result of resultQuery" :key="result.id">
      {{ result.title }}
    </div>
  </div>
</template>

<script>
export default{
  name: "App",
  data(){
    return {
      searchQuery: null,
      resources: [
        {id: 1, title: "javascript for dummies"},
        {id: 2, title: "vue for dummies"},
        {id: 3, title: "css for dummies"},
        {id: 4, title: "java for dummies"},
        {id: 5, title: "cisco for dummies"},
        {id: 6, title: "c++ for dummies"},
      ]
    }
  },
  computed: {
    resultQuery(){
      if (this.searchQuery) {
        return this.resources.filter(item => {
          return this.searchQuery
          .toLowerCase()
          .split("")
          .every(v => item.title.toLowerCase().includes(v));
        });
    }else{
      return this.resources;
    }}
  }

}
</script>
<style>
</style>