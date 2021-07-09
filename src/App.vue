<template> 

  <div class="shopping-list">
    <h1> {{ header }} </h1>

    <input type="text" v-model="newitems" placeholder="Add a new item" v-on:keyup.enter="items.push({id:items.lenght + 1 , newitems }['newitems'])">

    <ul>
      <li v-for="item in items" :key="item" @click="items.splice(items, 1)">
      
        {{item}}
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'App',
  
  data() {
    return {
      header: "Shoppie List 🛒",
      newitems: [
        
      ],
      items: [
        
      ] ,
    }
  },
  mounted() {
    if (localStorage.getItem('items')) this.items = JSON.parse(localStorage.getItem('items'));
  },
  watch: {
    items: {
      handler() {
      localStorage.setItem('items', JSON.stringify(this.items));
    },
    deep: true,
    }
  },
}


</script>

<style>
  @import './app.css';
</style>
