<template>
    <span>
        <home-content></home-content>
        <investments-and-debts></investments-and-debts>
    </span>
</template>

<script>
import HomeContent from '@/components/HomeContent';

export default {
    name: 'home',
    components: {
        HomeContent
    }
};
</script>
