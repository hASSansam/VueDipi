<template>
<h1>dipi mi piace il pipi</h1>
</template>
<script>

export default {
  name: 'HomeView',
  data() {
    return {
      items: [],
      selected: []
    }
  },
  methods: {
    getProdotti() {
      if(localStorage.getItem("items")==null){
      fetch('https://fakestoreapi.com/products')
        .then((res) => res.json())
        .then((json) => {
          
          for(let i=0;i<json.length;i++){
          json[i].stock=Math.floor(Math.random() * 100);
          }
          this.items = json
          localStorage.setItem("items",JSON.stringify(this.items))
        })
      }
      else{
        this.items = JSON.parse(localStorage.getItem("items"))
      }
    },
    cart() {
      localStorage.setItem("selected",JSON.stringify(this.selected))
    }
  },
  mounted() {
    this.getProdotti();
    
  }
}
</script>
