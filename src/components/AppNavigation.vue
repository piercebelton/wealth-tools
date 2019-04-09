<template>
    <span>
        <v-toolbar app color="blue darken-4" dark>
            <v-toolbar-title>{{appTitle}}</v-toolbar-title>
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
</style>
