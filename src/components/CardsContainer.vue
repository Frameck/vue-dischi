<template>
    <div class="cards-container">
        <SelectFilter :genre="getAllGenre" @filterMade="setFilterValue"></SelectFilter>
        <Card v-for="album,i in filteredAlbums" :key="i"
        :url="album.poster"
        :title="album.title"
        :author="album.author"
        :year="album.year"
        ></Card>
    </div>
</template>

<script>
import axios from "axios";
import Card from './Card.vue';
import SelectFilter from './SelectFilter.vue';

export default {
    name: 'CardsContainer',
    components: {
        Card,
        SelectFilter
    },
    data() {
        return {
            url: 'https://flynn.boolean.careers/exercises/api/array/music',
            albumsList: [],
            filterValue: ''
        }
    },
    methods: {
        fetchApiData(url) {
            axios.get(url).then(res => {
                if (res.status !== 200) {
                    return this.albumsList = 'Ops, qualcosa è andato storto'
                }
                this.albumsList = res.data.response
            })
        },
        setFilterValue(genreSelected) {
            this.filterValue = genreSelected
        }
    },
    mounted() {
        this.fetchApiData(this.url)
    },
    computed: {
        getAllGenre() {
            const allGenre = []

            this.albumsList.forEach(album => {
                const { genre } = album

                if (allGenre.includes(genre)) return
                
                allGenre.push(genre)
            })

            console.log(allGenre)
            return allGenre
        },
        filteredAlbums() {
            if (!this.filterValue) {
                console.log(this.filterValue)
                return this.albumsList
            }

            console.log(this.filterValue)

            const filteredAlbums = this.albumsList.filter(album => 
                album.genre === this.filterValue
            )

            console.log(filteredAlbums)

            return filteredAlbums
        }
    }
}
</script>

<style>

</style>