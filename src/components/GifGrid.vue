<template src='./templates/GifGrid.html'></template>

<script>
import GifBox from './GifBox.vue'
export default {
    name: 'GifGrid',
    props: ['gifs'],
    components: {GifBox}
}
</script>

<style scoped>

</style>