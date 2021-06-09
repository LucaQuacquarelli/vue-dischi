<template>
    <main v-if="!loader">
        <div class="album-container">
            <Album v-for="(album,index) in albums" :key="index"
            :cover="album.poster"
            :title="album.title"
            :author="album.author"
            :year="album.year"/>
        </div>
    </main>
    <div v-else class="loader">
        <Loader/>
    </div>
</template>

<script>
import Album from './Album';
import Loader from './Loader';
import axios from 'axios';

export default {
    name: "Main",
    components: {
        Album,
        Loader
    },
    data: function() {
        return {
            apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
            albums: [],
            loader: true
        }
    },
    created: function() {
        axios
            .get(this.apiUrl)
            .then(
                (response)=> {
                    this.albums = response.data.response
                    setTimeout(
                        () => {
                            this.loader = false
                        },3000)
                    
                }
            )
    }
}
</script>

<style lang="scss" scoped>
    main {
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 50px;
        background-color: #1e2d3b;

        .album-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            flex-basis: 60%;
        }
    }
    .loader {
        text-align: center;
    }
</style>