<template>
  <div id="app">
    <HeaderComp />
    <AddGroceryItemComp v-on:add-grocery="addGrocery"/>
    <GroceryItemsComp v-bind:GroceryList="GroceryList" v-on:del-GroceryItem="deleteGroceryItem"/>
  </div>
</template>

<script>
import HeaderComp from './components/layout/HeaderComp'
import AddGroceryItemComp from './components/AddGroceryItemComp'
import GroceryItemsComp from './components/GroceryItemsComp'
import axios from 'axios'
export default {
  name: 'app',
  components: {
    GroceryItemsComp,
    HeaderComp,
    AddGroceryItemComp
  },
data: function(){
  return{
    GroceryList: []
  }
},
methods:{
    deleteGroceryItem(id){
      this.GroceryList = this.GroceryList.filter(GroceryItem => GroceryItem.id !== id);
    },
    addGrocery(grocery){
      const {title, completed} = grocery;
      axios.post("https://jsonplaceholder.typicode.com/todos", {title, completed})
      .then(res => this.GroceryList = [...this.GroceryList, res.data])
      .catch(err=>alert(err))
     //this.GroceryList = [...this.GroceryList, grocery];
    }
  },
  created(){
    axios.get("https://jsonplaceholder.typicode.com/todos?_limit=10")
    .then(res => this.GroceryList = res.data)
    .catch(err => alert(err))
  }
}
</script>
<style>
* {
  box-sizing:border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family:Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  line-height: 1.4;
}
</style>
