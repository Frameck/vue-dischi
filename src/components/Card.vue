<template>
    <div class="card">
        <img :src="url" :alt="title">
        <div class="card-body">
            <h4 class="title">{{ title.toUpperCase() }}</h4>
            <span>{{ author }}</span>
            <span>{{ year }}</span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        url: String,
        title: String,
        author: String,
        year: String
    }
}
</script>

<style>

</style>