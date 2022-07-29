<template>
<div>
    <h1><u>My Second CRUD Operation</u></h1>
    <form>
        <label for="Name">Name</label><br>
        <input type="text" id="Name" name="Name" ><br>
        <label for="Place">Place</label><br>
        <input type="text" id="Place" name="Place" ><br>
        <label for="Email">Email</label><br>
        <input type="email" id="Email" name="Email" ><br>
        <label for="Password">Password</label><br>
        <input type="password" id="Password" name="Password" ><br>
        <label for="Comany">Company</label><br>
        <input type="text" id="Company" name="Comapny" ><br>
        <input type="submit" value="Submit"><input type="reset" value="Reset">
    </form>
    <table>
        <tr>
            <td>Name</td>
            <td>Place</td>
            <td>Email</td>
            <td>Password</td>
            <td>Company</td>
        </tr>
        <tr v-for="item in users" :key="item">
            <td>{{item.Name}}</td>
            <td>{{item.Place}}</td>
            <td>{{item.Email}}</td>
            <td>{{item.Password}}</td>
            <td>{{item.Company}}</td>
            <td><button></button></td>
        </tr>
    </table>
</div>
</template>

<script>
export default {
}
</script>

<style scoped>
div {
    background-color: rgb(222, 187, 135);
    text-align: center;
    margin: 20; 
    /* padding: 45pc; */
     height: 600px; 
}
.name {
    font-display: initial
}
</style>