<template>
    <div class="cards-container">
        <Card v-for="album,i in albumsList" :key="i"
        :url="album.poster"
        :title="album.title"
        :author="album.author"
        :year="album.year"
        ></Card>
    </div>
</template>

<script>
import axios from "axios";
import Card from './Card.vue'

export default {
    name: 'CardsContainer',
    components: {
        Card
    },
    data() {
        return {
            url: 'https://flynn.boolean.careers/exercises/api/array/music',
            albumsList: []
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
        }
    },
    mounted() {
        this.fetchApiData(this.url)
    }
}
</script>

<style>

</style>