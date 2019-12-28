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
export default {
  name: 'app',
  components: {
    GroceryItemsComp,
    HeaderComp,
    AddGroceryItemComp
  },
data: function(){
  return{
    GroceryList: [
      {
        id: 1,
        title: "Milk",
        quantity: "1 liter",
        completed: false
      },
      {
        id: 2,
        title: "Eggs",
        quantity: "3",
        completed: true
      },
      {
        id: 3,
        title: "Fries",
        quantity: "1 kg",
        completed: true
      }
    ]
  }
},
methods:{
  deleteGroceryItem(id){
    this.GroceryList = this.GroceryList.filter(GroceryItem => GroceryItem.id !== id);
  },
  addGrocery(grocery){
    this.GroceryList = [...this.GroceryList, grocery];
  }
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
