<template>
    <span>
      <investments-and-debts></investments-and-debts>
    </span>
</template>
<script>
import InvestmentsAndDebts from '@/components/InvestmentsAndDebts';

export default {
    name: 'Menu',
    components: {
      InvestmentsAndDebts
    }
};
</script>
<style scoped>
</style>
