<template>
  <section class="container">
    <!-- <div>
      <header-ini />
      <logo-gw />
      <h1 class="title">
        belajar-nuxt
      </h1>
      <h2 class="subtitle">
        belajar nuxt pertama kali
      </h2>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          class="button--green"
        >Documentation</a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey"
        >GitHub</a>
      </div>
    </div> -->
    <div>
        <input-data />
        <search-data />
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Header from '~/components/Header.vue'
import axios from 'axios'
import inputdata from '~/components/inputdata.vue'
import searchdata from '~/components/searchdata.vue'

export default {
  components: {
    'logo-gw': Logo,
    'header-ini': Header,
    'input-data' : inputdata,
    'search-data' : searchdata
  },
  data() {
        return {
        }
  },
  mounted() {

  },
  methods: {
        
    }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.form {
  display: inline-block;
  align-items: left;
  margin: 10px;
}
</style>
