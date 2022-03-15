<template>
<div class="madlibs">
 <p v-show="!card.isReversed">{{card.meaning_up.split(",")[1]}}</p>
<p v-show="card.isReversed">{{card.meaning_rev.split(",")[1]}}</p>
</div>
</template>
<script>

export default {
    name: "Madlibs",
    props:{
        card: Object,
    }
}
</script>
<style scoped>

</style>