<template>
<div>
    <div v-for="r in result" :key="r.id">
        <!-- <div>{{r.id}}</div> -->
        <div>
        {{r.name}}
        <img :src="r.image.small" alt="">
        </div>
        <div>

        {{r.hashing_algorithm}}
        </div>
        <div>
            <h2 v-html="r.description.en">
            </h2>
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
           async mounted() {  
                const resu = await axios.get(`https://api.coingecko.com/api/v3/coins/${this.id}`)
                console.log(resu.data);
                this.result.push(resu.data);
                console.log(this.result);
                return resu.data
                
            },
}
</script>

<style scoped>
</style>