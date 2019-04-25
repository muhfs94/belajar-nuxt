<template>
<section class="container">
    <div>
        <ini-header />
        <ini-logo />
        <div>
            {{ nama }}
        </div>
        <div>
            <button v-on:click="reverseName">Reverse your name</button>
        </div>
    </div>
</section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Header from '~/components/Header.vue'

export default {
    components: {
        'ini-logo': Logo,
        'ini-header': Header
    },
    data() {
        return {
            nama: "Muhammad",
        }
    },
    methods: {
        reverseName() {
            this.nama = this.nama.split('').reverse().join('');
        }
    }
}
</script>
