<script setup>

const props = defineProps(["url"])
</script>

<template>
    <img class="image" :src="props.url" >
</template>


<style scoped>
    .image{
        max-width: 150px;
        max-height: 150px;
        margin: 5px;
        border: 2px solid red;
    }
</style>