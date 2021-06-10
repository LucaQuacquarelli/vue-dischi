<template>
    <main v-if="!loader">
        <div class="filter-container">
            <label for="genre">Genere :</label>
            <FilterGenre @findGenre="setGenre"/>
            <label for="Author">Autore :</label>
            <FilterAuthor @findGenre="setGenre"/>
        </div>
        <div class="album-container">
            <Album v-for="(album,index) in filteredGenre" :key="index"
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
import FilterGenre from './FilterGenre.vue'
import FilterAuthor from './FilterAuthor.vue';

export default {
    name: "Main",
    components: {
        Album,
        Loader,
        FilterGenre,
        FilterAuthor
    },
    data: function() {
        return {
            apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
            albums: [],
            loader: true,
            sectionValue: ""
        }
    },
    computed: {
        filteredGenre: function() {

            if (this.sectionValue == "all") {
                return this.albums;
            }

            const newArray = this.albums.filter(
                (element) => {
                    return element.genre.toLowerCase().includes(this.sectionValue.toLowerCase()) || element.author.toLowerCase().includes(this.sectionValue.toLowerCase())
                } 
            );
            return newArray;
        },
    },    
    methods: {
        setGenre(selected) {
            this.sectionValue = selected
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
@import '../style/variables';
    main {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 50px;
        background-color: $main-bg-color;

        .filter-container {

            margin: 10px 0;

            label {
                margin: 0 10px;
                color: $font-white;
            }

        }

        .album-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            padding: 0 250px;
        }
    }
    .loader {
        text-align: center;
    }
</style>