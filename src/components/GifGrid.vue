<template>
    <div v-if="gifs">
      <div v-for="gif in gifs" v-bind:key="gif.id">
        <GifBox :gif="gif"></GifBox>
      </div>
    </div>
</template>

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