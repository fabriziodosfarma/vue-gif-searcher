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

<style scoped src='./GifBox.scss' lang='scss'>

</style>