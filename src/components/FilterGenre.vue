<template>
    <select name="genre"
    v-model="selected"
    @change="$emit('findGenre', selected)">
        <option value="" disabled selected>Seleziona Genere</option>
        <option value="all">All</option>
        <option value="rock">Rock</option>
        <option value="pop">Pop</option>
        <option value="jazz">Jazz</option>
        <option value="metal">Metal</option>
    </select> 
</template>

<script>
export default {
    name: "FilterGenre",
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