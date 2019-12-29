<template>
    <header class="header">
        <h1>Grocery List</h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
    </header>
</template>
<script>
export default {
    name: "Header"
}
</script>
<style scoped>
.header{
    background: rgba(255, 241, 44, 0.836);
    color: rgb(65, 65, 65);
    text-align: center;
    padding: 0px;
}
</style>