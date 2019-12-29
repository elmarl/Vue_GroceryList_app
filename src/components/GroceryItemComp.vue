<template>
    <div class="todo-item" v-bind:class="{'completed':GroceryItem.completed}" >
      <p>
        <input type="checkbox" v-on:change="markComplete" v-model="GroceryItem.completed">
        {{GroceryItem.title}}
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
.todo-item {
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
border: none;

}
</style>
