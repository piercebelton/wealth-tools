<template>
    <span>
        <v-toolbar app color="blue darken-4" dark>
          <router-link to="/">
              <v-toolbar-title>{{appTitle}}</v-toolbar-title>
            </router-link>
        </v-toolbar>
    </span>
</template>

<script>
export default {
    name: 'AppNavigation',
    data() {
        return {
            appTitle: 'Wealth Tools'
        };
    }
};
</script>

<style scoped>
a {
    color: white;
    text-decoration: none;
}
</style>
