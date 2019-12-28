<template>
    <div>
        <form @submit="addGrocery">
            <input type="text" v-model="title" name="title" placeholder="Add Groceries">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
import uuid from 'uuid';
export default {
    name: "AddGroceries",
    data(){
        return{
            title:''
        }
    },
    methods:{
        addGrocery(e){
            e.preventDefault();
            const Grocery = {
                id: uuid.v4(),
                title: this.title,
                completed: false,
                quantity:"1"
            }
            this.$emit('add-grocery', Grocery);
            this.title = ""
        }
    }
}
</script>

<style scoped>
form{
    display: flex;
}
input[type="text"]{
    flex:10;
    padding: 5px;
}
input[type="submit"]{
    flex:2;
}
</style>