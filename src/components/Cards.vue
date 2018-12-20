<template>
    <div>
        <head>
            <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.6.1/css/all.css" integrity="sha384-gfdkjb5BdAXd+lj+gudLWI+BXq4IuLW5IT+brZEZsLFm++aCMlF1V92rMkPaX4PP" crossorigin="anonymous">
        </head>
        <div class="card-wrapper">
            <div class="card" v-for="show in tvShows" :key="show.show.id">
                <a :href="show.show.url">
                    <img :src="show.show.image.medium" alt="poster">
                </a>
                <div class="card-content">
                    <h1>{{show.show.name}}</h1>
                    <div class="rating-wrapper">
                        <i class="fas fa-star"></i><p class="rating" v-if="show.show.rating.average">{{show.show.rating.average}}</p><p class=" rating" v-else>-</p>
                    </div>
                </div>
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
    props: {
        search: String,
        tvShows: Array
    },
    methods: {
        fetchTvShows: function() {
            fetch(`http://api.tvmaze.com/search/shows?q=:friends`)
            .then(response => response.json())
            .then(response => {
                this.TvShows.push(...response)
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
    height: 330px;
    width: 150px;
    display: flex;
    flex-direction: column;
    margin: 15px;
}

h1 {
    font-size: 16px;
}

img {
    width: 150px;
}

a {
    text-decoration: none;
}

.rating-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
}

.rating {
    margin: 0;
    padding-top: 3px;
}

i {
    margin: 5px;
}
</style>
