<template>
    <div>
        <form @submit="addGrocery">
            <input type="text" v-model="title" name="title" placeholder="Add Groceries">
            <input type="submit" value="Submit" class="myButton">
        </form>
    </div>
</template>

<script>
//import uuid from 'uuid';
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
                //id: uuid.v4(),
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
    border-style: hidden;
}
input[type="text"]:focus {
     outline:none;
}
input[type="submit"]{
    flex:2;
}
.myButton {
	box-shadow:inset 0px 1px 0px 0px #ffffff;
	background:linear-gradient(to bottom, #ededed 5%, #dfdfdf 100%);
	background-color:#ededed;
	border-radius:6px;
	border:1px solid #dcdcdc;
	display:inline-block;
	cursor:pointer;
	color:#777777;
	font-family:Arial;
	font-size:15px;
	font-weight:bold;
	padding:6px 24px;
	text-decoration:none;
	text-shadow:0px 1px 0px #ffffff;
}
.myButton:hover {
	background:linear-gradient(to bottom, #dfdfdf 5%, #ededed 100%);
	background-color:#dfdfdf;
}
.myButton:active {
	position:relative;
	top:1px;
}
</style>