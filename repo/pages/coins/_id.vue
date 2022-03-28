<template>
<div>
    <div v-for="r in result" :key="r.id">
        <div>
        {{r.name}}
        <img :src="r.image.small" alt="">
        </div>
        <div>

        {{r.hashing_algorithm}}
        </div>
        <div>
        {{r.description.en}}
        </div>
    </div>
</div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            id : this.$route.params.id,
            result : []
        }
    },
            computed : {
                res : async function(id) {
                          const resu = await axios.get(`https://api.coingecko.com/api/v3/coins/${this.id}`)
                          console.log(resu.data);
                          this.result.push(resu.data);
                          console.log(this.result);
                          return resu.data
                }
            },
}
</script>

<style scoped>
</style>