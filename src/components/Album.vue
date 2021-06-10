<template>
    <div class="album">
        <img :src="cover" :alt="title">
        <h4>{{title}}</h4>
        <span>{{author}}</span>
        <span>{{year}}</span>
    </div>
</template>

<script>
export default {
    name: "Album",
    props: {
        cover: String,
        title: String,
        author: String,
        year: String
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables';

    .album {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 120px;
        margin: 10px;
        padding: 10px;
        text-align: center;
        background-color: $spotify-bg-theme;

        img {
            width: 100%;
        }

        h4 {
            margin: 10px 0;
            color: $font-white;
        }   

        span {
            font-size: 12px;
            color: #7b7f80;
        }
    }

</style>