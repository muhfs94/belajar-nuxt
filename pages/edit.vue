<template>
    <div>
        <h3> Form Edit User</h3>
        <form @submit.prevent="updateUser">
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
            <button v-on:click="deleteUser">Delete</button>
            </p>
        </form>
    </div>
</template>

<script>
import axios from 'axios'
import searchName from '~/components/searchdata.vue'

export default {
    components: {
        'searchName' : searchName
    },
    data: {
            name: this.searchName,
            age: this.age,
            address: this.address,
            
    },
    mounted() {

    },
    methods: {
        updateUser(name, age, address) {
            axios.put('http://localhost:4000/users' + name, {
                age: this.age,
                address: this.address
            })
            .then(res => {
                window.location.reload()
            })
            .catch(err => {
                console.log(err)
            })
        },
        deleteUser(users, id) {
            axios.delete('http://localhost:4000/users' + id)
            .then((res) => {
                this.users.splice(id, 1)
                window.location.reload()
            })
            .catch((err) => {
                console.log(err)
            })
        }
    }
}
</script>

<style lang="">
    
</style>