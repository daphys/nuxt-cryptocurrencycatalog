<template>
  <div>
    <h1>Welcome to Cryptonomicon</h1>
  

    <div v-for="i in ip" :key="i">
      <div class="elem">
      <h1>{{i.name}}</h1>
      </div> 
    </div>

  </div>
</template>

<script>
import Get from '/components/Get.vue'
import axios from 'axios'
export default {
  async asyncData({ $axios }) {
    const ip = await $axios.$get('https://api.coingecko.com/api/v3/coins/list')
    return { ip }
  },
  components: {
    Get,
  },
  data() {
    return {}
  },
  methods: {},
}
</script>

<style scoped>
  .elem {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: 10px;
    padding: 10px;
    border: 1px solid black;
  
  }
</style>
