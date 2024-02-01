<template>
    {{ userId }}
    <h1>dipi mi piace il pipi</h1>
    </template>
    <script>
    
    export default {
      name: 'HomeView',
      data() {
        return {
            userId: 0,
        }
      },
      methods: {
  
      },
      mounted() {
        this.userId = parseInt(this.$route.params.id);
        
      }
    }
    </script>
    