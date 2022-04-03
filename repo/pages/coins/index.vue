<template>
  <div class="elemCont">
    <div v-for="i in ip" :key="i.id">
      <div @click.prevent="open(i)" class="elem">
      <h1>{{i.name}}</h1>
      </div> 
    </div>

  </div>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData({ $axios }) {
    const ip = await $axios.$get('https://api.coingecko.com/api/v3/coins/list')
    return { ip }
  },
  components: {
  },
  data() {
    return {}
  },
  methods: {
     open(i) {
       this.$router.push(`/coins/${i.id}`)
    }
  },
}
</script>

<style scoped>
.elemCont{
  display: grid;
  grid-template-columns: 1fr 1fr;
}
  .elem {
    justify-content: center;
    align-items: center;
    margin: 10px;
    padding: 10px;
    border: 1px solid black;
  
  }
</style>
