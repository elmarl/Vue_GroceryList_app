<template>
    <div class="grc-item" v-bind:class="{'completed':GroceryItem.completed}" >
      <p>
        <input type="checkbox" v-on:change="markComplete" :checked="GroceryItem.completed">
        <span class="title">{{GroceryItem.title}}</span>
        <button class="del" @click="$emit('del-GroceryItem', GroceryItem.id)">Remove</button>
        </p>
    </div>
</template>

<script>
export default {
    name:"GroceryItem",
    props:{
      GroceryItem: Object
    },
    methods: {
      markComplete(){
        this.GroceryItem.completed = !this.GroceryItem.completed
      }
    }
}
</script>

<style scoped>
p{
  align-content: flex-start;
}
.title{
margin-left: 5px;
}
.grc-item {
  display: flex;
  background: white;
  padding: 10px;
  border-bottom: line-through;
}
.completed {
  text-decoration: line-through;
}
.del {
background-color:#ff5c407a;
border-radius: 30%;
display: inline-block;
margin-left: 5px;
border: none;
}
</style>
