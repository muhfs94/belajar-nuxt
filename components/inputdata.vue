<template>
    <div>
        <h3> Form Input</h3>
        <form @submit.prevent="onSubmit" autocomplete="off">
            <div class="form-group">
              <label for="name">Name:</label>
              <input v-model="name" id="name" >
            </div>
            <div class="form-group">
              <label for="age">Age : </label>
              <input v-model="age" id="age">
            </div>
            <div class="form-group">
              <label for="address">Address : </label>
              <input v-model="address" id="address"></input>
            </div>
            <button type="submit" value="Submit">Submit</button>
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