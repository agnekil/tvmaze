<template>
    <div class="header">
        <div class="welcome-message">{{msg}}</div>
        <div class="search-field">
            <input type="text" placeholder="Search shows and people">
            <button>Search</button>
        </div>
        <div class="menu">
            <ul>
                <li>Shows</li>
                <li>People</li>
                <li>Schedule</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "Header",
    props: {
        msg: String
    }
}
</script>

<style scoped>
* {
    box-sizing: border-box;
}

.header {
    background-color: lightblue;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

input {
    border-top-left-radius: 50px;
    border-bottom-left-radius: 50px;
    height: 32px;
    width: 350px;
    border: none;
    padding-left: 10px;
    background-color: rgb(236, 236, 236);
    margin: 20px 0px;
}

button {
    border-top-right-radius: 20px;
    border-bottom-right-radius: 20px;
    height: 32px;
    width: 90px;
    padding: 8px;
    border: none;
    background-color: grey;
}

.welcome-message {
    font-size: 30px;
    margin: 30px;
}

.menu {
    background-color: rgb(235, 235, 235);
    height: 50px;
    display: flex;
    justify-content: center;
    width: 100%;
}

ul {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    list-style-type: none;
    margin: 0;
    padding: 0;
    width: 350px;
}

</style>
