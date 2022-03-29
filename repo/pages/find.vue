<template>
  <div>
    <input v-model="dataFromInput" type="text" />
    <button @click="getData">+</button>
    <div v-for="r in resp" :key="r.id">
      <div class="mainContainer">
          <div class="coinImg">
          <img :src="r.image.small" alt="">
          </div>
          <div>
        <h2>
          name: {{ r.name }}
        </h2>
        <h2>
          id: {{ r.symbol }}
        </h2>
        <h2>
          Alghoritm : {{ r.hashing_algorithm }}
          </h2>
        <h2 v-html="r.description.en"></h2>
          </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      dataFromInput: [],
      resp: [],
    }
  },
  methods: {
    async getData(dataFromInput, resp) {
      try {
        const res = await axios.get(
          `https://api.coingecko.com/api/v3/coins/${this.dataFromInput}`
        )
        console.log(res);
        if (this.resp.length >= 1) {
            this.resp.length = 0;
            console.log('13')
        } 
        else{
            this.resp.push(res.data) ;
            this.dataFromInput = '' ; 
        } 
         }catch (error) {
            console.log(error)
            this.dataFromInput = ''
      }
    },
  },
}
</script>

<style scoped>
.mainContainer {
  display: grid;
  gap: 30px;
}
.coinImg{
    padding: 30px;
    border: 1px solid;
    max-width: 50px;
    width: 100%;
}
</style>