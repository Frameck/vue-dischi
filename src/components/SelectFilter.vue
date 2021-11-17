<template>
    <div class="selectFilter">
        <select name="filterByGenre" id="filter" v-model="filterValue" @change="startFilter">
            <option v-for="genre,i in genre" :key="i" :value="genre">{{ genre }}</option>
        </select>
    </div>
</template>

<script>
export default {
    name: 'SelectFilter',
    props: {
        genre: Array
    },
    data() {
        return {
            filterValue: '',
            filterActive: '',
        }
    },
    methods: {
        startFilter() {
            console.log("avvio la ricerca", this.filterValue)
            this.filterActive = this.filterValue
            this.$emit("filterMade", this.filterActive)
        },
        resetFilter() {
            this.filterValue = ''
            this.filterActive = ''
            this.$emit("resetMade")
        }
    }
}
</script>

<style>

</style>