<template>
<div>
    <div class="mainContainer">
    <div v-for="r in result" :key="r.id">
        <!-- <div>{{r.id}}</div> -->
        <div>
            <h2>
        Name: {{r.name}}
            </h2>
        <br>
        <img :src="r.image.large" width="150px" alt="">
        </div>
        <div>
            <h2>
        Algorithm: {{r.hashing_algorithm}}
            </h2>
        </div>
        <div>
            <div style="font-size : 20px">
            <span>Description: </span>
            <span>
                <span v-if="r.description.en.length == 0">
                    No description
                </span>
                <span v-else v-html="r.description.en"></span>
            </span>
            </div>
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
.mainContainer{
    margin: 0 auto;
}
</style>