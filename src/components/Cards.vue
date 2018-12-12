<template>
<div class="card-wrapper">
    <div class="card" v-for="show in TvShows" :key="show.show.id">
        <a :href="show.show.url">
            <img :src="show.show.image.medium" alt="poster">
        </a>
        <div class="card-content">
            <h1>{{show.show.name}}</h1>
        </div>
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
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;

}

.card {
    background-color: rgb(235, 235, 235);
    height: 400px;
    width: 200px;
    display: flex;
    flex-direction: column;
    margin: 15px;
}

h1 {
    font-size: 20px;
}

img {
    width: 200px;
}

a {
    text-decoration: none;
}
</style>
