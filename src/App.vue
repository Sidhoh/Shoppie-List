<template> 

  <div>
    
    <div class="shopping-list">
      <h1> {{ header }} </h1>

      <input type="text" v-model="newitems" placeholder="Add a new item" v-on:keyup.enter="add(items, newitems)
    ">
    
      <ul>
        <li v-for="item in items" :key="item" @click="items.splice(items, 1)">
          {{item}}
        </li>
      </ul>
      <p v-if="items == 0">Congo! you bought all the items you listed</p>
    </div>


    <h2 class="footer">Made with ❤️, built with vue</h2>
  </div>

</template>

<script>

export default {
  name: 'App',
  methods: {
    add(items, newitems){
      items.push({id:items.lenght + 1 , newitems }['newitems'])
      this.newitems = ""
    }
  },
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
