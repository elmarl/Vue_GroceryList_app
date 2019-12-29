<template>

    <div>
        <div v-bind:key="GroceryItem.id" v-for="GroceryItem in GroceryList">
            <!--<h1>{{GroceryItem.title}}</h1>-->
            <GroceryItemComp class="grc" v-bind:GroceryItem="GroceryItem" v-on:del-GroceryItem="$emit('del-GroceryItem', GroceryItem.id)"/>
       </div>
    </div>
</template>
<script>
import GroceryItemComp from './GroceryItemComp.vue'
export default {
    name: "GroceryList",
    props: {
      GroceryList: Array
    },
    components:{
      GroceryItemComp
    }
}
</script>

<style scoped>
.grc {
  background-color: rgba(228, 228, 228, 0.61);
  border-bottom-style:dashed;
  border-bottom-width: 1px;
  border-bottom-color: rgb(83, 83, 83);
}
</style>
