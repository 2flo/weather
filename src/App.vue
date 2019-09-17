<template>
  <div id="app">
     <weather></weather>
  </div>
</template>

<script>
import weather from './components/weather.vue';

export default {
  name: 'app',
  components: {
    weather
  }
}
</script>

