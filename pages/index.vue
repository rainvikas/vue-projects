<template>
<div>
    <h1><u>My Second CRUD Operation</u></h1>
    <form @submit="addData">
        <label for="Name">Name</label><br>
        <input type="text" v-model="user.Name" id="Name" name="Name"><br>
        <label for="Place">Place</label><br>
        <input type="text" v-model="user.Place" id="Place" name="Place"><br>
        <label for="Email">Email</label><br>
        <input type="email" v-model="user.Email" id="Email" name="Email"><br>
        <label for="Password">Password</label><br>
        <input type="password" v-model="user.Password" id="Password" name="Password"><br>
        <label for="Company">Company</label><br>
        <input type="text" v-model="user.Company" id="Company" name="Company"><br>
        <label for="timestamp">Time</label><br>
        <input type="datetime" v-model="user.timestamp" id="timestamp" name="timestamp"><br>
        <input type="submit" @click="addData" value="Submit"><input type="reset" value="Reset">
    </form>
    <input type="submit" @click="deleteAll" value="DeleteAll">
    <table border="5px">
        <tr>
            <td>Name</td>
            <td>Place</td>
            <td>Email</td>
            <td>Password</td>
            <td>Company</td>
            <td>DataTime</td>
        </tr>
        <tr v-for="(item,index) in users" v-bind:index="index" :key="item">
            <td>{{item.Name}}</td>
            <td>{{item.Place}}</td>
            <td>{{item.Email}}</td>
            <td>{{item.Password}}</td>
            <td>{{item.Company}}</td>
            <td>{{item.timestamp}}</td>
            <td><button type="submit" @click="editData(index)">Edit</button></td>
            <td><button type="submit" @click="deleteData(index)">Delete</button></td>
        </tr>
    </table>
</div>
</template>
<script>
//import { thisTypeAnnotation } from '@babel/types';
export default {
    data() {
        return {
            users: [],
            user: {
                isEdit: true,
                editIndex: -1,
                // error:[],
                Name: '',
                Place: '',
                Email: '',
                Password: '',
                Company: '',
                timestamp:''
            }
        }
    },
    methods: {
        addData(event) {
            event.preventDefault();
            if (this.isEdit == true) {
                this.users[this.editIndex] = this.user;
                this.isEdit = false;
                this.editIndex = -1;
            } else {
                this.users.push(this.user);
            }
            this.user = {
                Name: '',
                Place: '',
                Email: '',
                Password: '',
                Company: '',
                timestamp:'',
            }
            console.log(this.users)
        },
        deleteData(index) {
            if (confirm('You Want To Delete The Data ?'))
                this.users.splice(index, 1);
        },
        editData(index) {
            this.user.Name = this.users[index].Name;
            this.user.Place = this.users[index].Place;
            this.user.Email = this.users[index].Email;
            this.user.Password = this.users[index].Password;
            this.user.Company = this.users[index].Company;
            this.user.timestamp = this.users[index].timestamp;
            this.isEdit = true;
            this.editIndex = index;
        },
        deleteAll() {
            if (confirm('Do you Want To Delete All The Data ?'))
                for (let i = 0; i < this.users.length; i++) {
                }
        },
        getNow: function () {
            const today = new Date();
            const date = today.getFullYear() + '-' + (today.getMonth() + 1) + '-' + today.getDate();
            const time = today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds();
            const dateTime = date + ' ' + time;
            this.timestamp = dateTime;
        }
    }
}
// VALIDATION:
//     checkForm: function (e) {
//   if (this.Name && this.Place && this.Email && this.Password && this.Company) {
//     return true;
//   }
//   this.errors = [];
//   if (!this.Name) {
//     this.errors.push('Name required.');
//   }
//   if (!this.Place) {
//     this.errors.push('Age required.');
//   }
//   if (!this.Place) {
//     this.errors.push('Age required.');
//   }
//   if (!this.Place) {
//     this.errors.push('Age required.');
//   }
//   if (!this.Place) {
//     this.errors.push('Age required.');
//   }
//   e.preventDefault();
// }
</script>
<style scoped>
div {
    background-color: rgb(205, 222, 135);
    text-align: center;
    /* margin: 20; */
    /* padding: 45pc; */
    height: 500px;
}
.name {
    font-display: initial
}
</style>