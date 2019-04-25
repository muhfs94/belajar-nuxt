<template>
    <div>
        <h3> Form Input</h3>
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
                window.location.reload()
            })
            .catch(err => {
                console.log(err)
            })
        },
    }
}
</script>

<style>

</style>