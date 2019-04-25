<template>
    <div>
        Form Input
        <form @submit.prevent="onSubmit">
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
        <div>
            <h3>Cari User</h3>
            <p>
            <label for="name">Name : </label>
            <input v-model="searchName" id="name"></p> 
            <button v-on:click="showUser">tampilkan user</button>
            <div v-for="(item, index) in user" :key="index">
            <p>Age : {{ item.age }} </p> 
            <p>Address :  {{ item.address }} </p>
            </div>
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
            searchName: ""
        }
    },
    mounted() {

    },
    methods: {
        onSubmit() {
            axios.post('http://localhost:4000/users', {
                name: this.name,
                age: this.age,
                address: this.address
            })
            .then(res => {

            })
            .catch(err => {
                console.log(err)
            })
        },
        showUser() {
            axios.get('http://localhost:4000/users', {
                params: {
                    name: this.searchName
                }
            })
            .then(res => {
                this.user = res.data
            })
            .catch(err => {
                console.log(err)
            })
        }
    }
}
</script>

<style>

</style>
