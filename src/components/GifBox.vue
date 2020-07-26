<template>
    <div class="gif-box">
        <img :src="gif.images.original.url">
    </div>
</template>

<script>
export default {
    name: 'GifBox',
    props: ['gif'],
}
</script>

<style scoped>
.gif-box {
    border-bottom: 1px #e8a87c solid;
    position: relative;
}
</style>