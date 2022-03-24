<template>
    <div>
        <input v-model="dataFromInput" type="text">
        <button @click="getData">+</button>
        <div v-for="r in response" :key="r">
            {{r.name}}
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            dataFromInput: [],
        }
    },
    methods: {
        async getData(dataFromInput) {
            const response = await axios.get(`https://api.coingecko.com/api/v3/coins/${this.dataFromInput}`)
            return response
        },
    },
    }
</script>

<style>

</style>