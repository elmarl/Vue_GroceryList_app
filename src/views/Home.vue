<template>
  <div id="app">
    <AddGroceryItemComp v-on:add-grocery="addGrocery"/>
    <GroceryItemsComp v-bind:GroceryList="GroceryList" v-on:del-GroceryItem="deleteGroceryItem"/>
  </div>
</template>

<script>
import AddGroceryItemComp from '../components/AddGroceryItemComp'
import GroceryItemsComp from '../components/GroceryItemsComp'
import axios from 'axios'
export default {
  name: 'Home',
  components: {
    GroceryItemsComp,
    AddGroceryItemComp
  },
data: function(){
  return{
    GroceryList: []
  }
},
methods:{
    deleteGroceryItem(id){
      axios.delete(`https://my-json-server.typicode.com/elmarl/grocery_list/groceries/${id}`)
      .then(res => this.GroceryList = this.GroceryList.filter(GroceryItem => GroceryItem.id !== id, res.data))
      .catch(err => alert(err))
    },
    addGrocery(grocery){
      const {title, completed} = grocery;
      axios.post("https://my-json-server.typicode.com/elmarl/grocery_list/groceries", {title, completed})
      .then(res => this.GroceryList = [...this.GroceryList, res.data])
      .catch(err=>alert(err))
    }
  },
  created(){
    axios.get("https://my-json-server.typicode.com/elmarl/grocery_list/groceries")
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
