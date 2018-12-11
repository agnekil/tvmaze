<template>
<div class="card-wrapper">
    <div class="card" v-for="show in TvShows" :key="show.show.id">
    <img :src="show.show.image.medium" alt="poster">
        <div class="card-image"></div>
        <div class="card-content">{{show.show.name}}</div>
    </div>
    </div>
</template>

<script>
export default {
    name: "Cards",
    data() {
        return {
        TvShows: []
        }
    },
    methods: {
        fetchTvShows: function() {
            fetch("http://api.tvmaze.com/search/shows?q=:suits")
            .then(response => response.json())
            .then(response => {
                this.TvShows.push(...response)
                console.log(this.TvShows)
            })
        }
    },
    created() {
        this.fetchTvShows()
    }
}
</script>

<style scoped>
.card-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
}

.card {
    background-color: rgb(235, 235, 235);
    height: 350px;
    width: 220px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: 20px;
}
</style>
