<template> 

  <div class="shopping-list">
    <h1> {{ header }} </h1>

    <input type="text" v-model="newitems" placeholder="Add a new item" v-on:keyup.enter="items.push({ newitems }['newitems'] )">

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
  
}


</script>

<style>
  @import './app.css';
</style>
