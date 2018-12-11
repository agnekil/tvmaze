<template>
<div class="card">
    <div class="card-wrapper" v-for="show in TvShows">
        <div class="card-image"></div>
        <div class="card-content" >{{show.show.name}}</div>
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
    background-color: rgb(235, 235, 235);
    height: 400px;
    width: 200px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
</style>
