<template>
    <div class="mainContainer">
        <div>
            <nuxt-link to="/">
          <h1>Cryptonomicon</h1>
            </nuxt-link>
        </div>
        <div class="elem">
            <nuxt-link to="/find">
            <h1>/ Find</h1>
            </nuxt-link>
        </div>
        <div class="elem">
            <nuxt-link to="/coins">
            <h1>/ Coins</h1>
            </nuxt-link>
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.mainContainer{
    display: flex;  
}
    .elem{
        margin-left: 15px;
    }

    a{
        text-decoration: none;
        color: black;
    }
</style>