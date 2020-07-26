<template>
    <div class="columns is-multiline grid is-vcentered has-background-primary" v-if="gifs">
      <div class="column is-one-quarter" v-for="gif in gifs" v-bind:key="gif.id">
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