<template>
<div>
<h1>Home Component</h1>
<button v-on:mouseover="hello('hello world')">Call hello function</button>
</div>
</template>
<script>
export default {
    name: "homePage",
    props:{
        data:String,
        msg:String
    },
    methods:{
        hello(data)
        {
            alert(data);
        }
    }
}
</script>

<style scoped>
h1{
    color: red;
}
</style>

