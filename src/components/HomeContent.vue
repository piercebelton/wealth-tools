<template>
    <v-container fluid fill-height class="home-content" style="max-height: 100vh;">
        <v-layout justify-center align-center column pa-5>
            <div class="display-4 font-weight-black white--text text-xs-center">WEALTH TOOLS</div>
            <div class="display-1 font-weight-bold white--text text-xs-center">See the effects of compound interest, instantly.</div>
            <v-btn class="mt-5 blue darken-4 white--text" to="/main">
              Get Started!
            </v-btn>
        </v-layout>
    </v-container>
</template>

<script>
export default {
    name: 'HomeContent'
};
</script>

<style scoped>
.home-content {
    background: url('https://source.unsplash.com/0jKuUj3vUTg');
    background-size: cover;
    width: 100%;
    height: 100%;
}
</style>
