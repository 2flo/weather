<template>
    <div class="weather">
        <div class="weatherbloc">
        City: <span v-if="info">{{info.name}}</span>
        <span><img :src="img_weather" alt="" width="150" height="150"></span>
        <span v-if="info">{{info.main.temp}}</span>
        <span v-if="info">{{info.weather[0].description}}</span>
    </div>
  <div class="weatherbloc">
        City: <span v-if="info">{{info.name}}</span>
        <span><img :src="img_weather" alt="" width="150" height="150"></span>
        <span v-if="infoNext">{{infoNext.list[8].main.temp}}</span>
        <span v-if="infoNext">{{infoNext.list[8].weather[0].description}}</span>
    </div>



    </div>
</template>

<script>

import axios from 'axios';

export default {
    name:"weather",
    data: function()
    { return {

        info: null,
        infoNext: null,
        main: null,
        mainnext: null,
    };
    },
    computed: {
        img_weather: function(){
            return this.info ? "https://openweathermap.org/img/wn/" + this.info.weather[0].icon + "@2x.png" : "";
        }
    },
    created() {
        axios
            .get("https://api.openweathermap.org/data/2.5/weather?q=London&units=metric&APPID=652be37c6135ed27ef8faa0d818e900c")
            .then(response=>(this.info = response.data) + (this.main = response.data))
        axios
            .get("http://api.openweathermap.org/data/2.5/forecast?q=London&units=metric&UK&APPID=652be37c6135ed27ef8faa0d818e900c")
            .then(response=>(this.infoNext=response.data) + (this.mainnext=response.data))
    }
}
</script>

<style>
.weatherbloc{
    display: flex;
    flex-direction: column;
    text-align: center;
    border: 1px solid black;
    padding: 15px;
    width: 25vw;
}
.img_weather{
    margin-left: 100px;
}
template{
    margin-left: 430px;
}
</style>
