<template>
    <div>
        <h3>Cari User</h3>
        <div class="form-group">
            <label for="name">Name : </label>
        <input v-model="searchName" id="name">
        </div>
        <button v-on:click="showUser()">tampilkan user</button>
        <div class="form-group">

        </div>
        

        <div v-if="result" v-for="(item, index) in user" :key="index">
            <p> User ID : {{ item.id }} </p>
            <p>Age : {{ item.age }} </p> 
            <p>Address :  {{ item.address }} </p>
            <button v-on:click="showEdit(item)">Edit</button>
            <button v-on:click="deleteUser(user, item.id)">Delete</button>
        </div>

        <div v-else>
            <form @submit.prevent="submitEdit">
                <h3>Edit User </h3>
                <p>User ID : {{ id }}</p>
                <p>
                <label for="name">Name : </label>
                <input v-model="name" id="name">
                </p>
                <label for="age">Age : </label>
                <input v-model="age" id="age">
                <p>
                <label for="address">Address : </label>
                <textarea v-model="address" id="address"></textarea>
                </p>
                <p>
                <input type="submit" value="Submit">
                </p>
            </form>

        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    components: {

    },
    data() {
        return {
            name: "",
            age: "",
            address: "",
            user: "",
            searchName: "",
            id:"",
            result: true,
        }
    },
    methods: {
        showUser() {
            this.result = true;
            axios.get('http://localhost:4000/users', {
                params: {
                    name: this.searchName
                }
            })
            .then(res => {
                this.user = res.data;
            })
            .catch(err => {
                console.log(err)
            })
        },
        showEdit(item) {
            this.result = false;
            this.id = item.id;
        },
        submitEdit(id, name, age, address) {
            axios.put('http://localhost:4000/users/' + this.id, {
                name: this.name,
                age: this.age,
                address: this.address
            })
            .then(res => {
                console.log(res)
            })
            .catch(err => {
                console.log(err)
            })
        },
        // deleteUser(item) {
        //     this.id = item.id;
        //     dels();
        // },
        deleteUser(user, id) {
            axios({
                method: 'DELETE',
                url: 'http://localhost:4000/users/' + id,
            })
            .then(res => {
                this.user.splice(id, 1)
                window.location.reload()

            })
            .catch(err => {
                console.log(err)
            })
        }
    }
}

</script>