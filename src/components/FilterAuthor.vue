<template>
    <select name="genre"
    v-model="selected"
    @change="$emit('findGenre', selected)">
        <option value="" disabled selected>Seleziona Autore</option>
        <option value="all">All</option>
        <option value="bon jovi">Bon Jovi</option>
        <option value="queen">Queen</option>
        <option value="sting">Sting</option>
        <option value="steve gadd band">Steve Gadd Band</option>
        <option value="iron maiden">Iron Maiden</option>
        <option value="eric clapton">Eric Clapton</option>
        <option value="deep purple">Deep Purple</option>
        <option value="metallica">Metallica</option>
        <option value="dave weckl">Dave Weckl</option>
        <option value="michael jacjson">Michael Jacjson</option>
    </select> 
</template>

<script>
export default {
    name: "FilterAuthor",
    data: function() {
        return {
            selected: ""
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables';
    select {
        
        padding: 5px 10px;
        border: 3px solid #1ed760;
        border-radius: 35px;
        background-color: transparent;
        color: $font-white;
        
        option {
            background-color: $main-bg-color;
        }
    }
</style>