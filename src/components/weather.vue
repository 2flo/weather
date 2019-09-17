<template>
    <div class="weather">
        <h2>La météo de votre ville</h2>
        City: <span v-if="info">{{info.city.name}}</span>
        <img :src="img_weather" alt="">
        <span v-if="info">{{info.list[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 21].main.temp}}</span>
        <span v-in="info">{{info.list[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31].weather[0].description}}</span>
    </div>
</template>

<script>

import axios from 'axios';

export default {
    name:"weather",
    data: function()
    { return {

        info: null
    }
    },
    computed: {
        img_weather: function(){
            return this.info ? "https://openweathermap.org/img/wn/"+this.info.list[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30 ,31].weather[0].icon +"@2x.png" : ""
        }
    },
    created() {
        axios
            .get("http://api.openweathermap.org/data/2.5/forecast?q=London&units=metric&UK&APPID=652be37c6135ed27ef8faa0d818e900c")
            .then(response=>(this.info=response.data))
    }
}
</script>

<style>
.weather{
    display: flex;
    flex-direction: column;
    text-align: center;
}

img{
    width: 40%;
    height: 300px;
    margin-left: 430px;
}
</style>
