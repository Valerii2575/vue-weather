<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>

<template>
  <div class="weather" :class="weatherClass">
    <div class="container">
      <div class="card weather-form">
        <input type="text" class="weather-form_input"
              v-model="searchQuery"
              placeholder="Enter city">
              <button class="weather-form_btn"
                      @click="weatherSearch">
                      Search
              </button>
      </div>

      <div class="card weather-load" v-if="loading">
        Loader....
      </div>

      <div class="card" v-if="error">Error</div>

      <div class="weather-info" v-show="!error && location && temperature !== 0 && description">
        <div class="weather-info_text">
          <p class="card">{{ location }}</p>
          <p class="card">{{ temperature }} &deg;C</p>
          <p class="card">{{ description }}</p>
        </div>
      </div>
    </div>

    <div class="weather-bg">
      <div>
        <img class="weather-bg_img bg" src="./assets/earth.jpg" alt="">
        <img class="weather-bg_img sunny-sky" src="./assets/sunny-sky.jpg" alt="">
        <img class="weather-bg_img overcast" src="./assets/overcast.jpg" alt="">
        <img class="weather-bg_img partly-cloudy" src="./assets/partly-cloudy.jpg" alt="">
      </div>
    </div>

  </div>
</template>
<script>
  export default {
    data(){
      return {
        location: '',
        temperature: 0,
        description: '',
        loading: false,
        error: false,
        searchQuery: '',
      };
    },
    computed: {
      weatherClass(){
        if(this.description.includes('Sunny')){
          return 'sunny-sky';
        }
        else if(this.description.includes('Overcast')){
          return 'overcast';
        }
        else if(this.description.includes('Partly Cloudy') || this.description.includes('Partly cloudy')){
          return 'partly-cloudy';
        }
        else {
          return '';
        }
      }

    },
    methods: {
      weatherSearch(){
        this.loading = true;
        this.error = false;
        fetch(`http://api.weatherapi.com/v1/current.json?key=6d1386f611584dedb9772458252104&q=${this.searchQuery}`)
        .then(response => response.json())
        .then(data => {
          this.loading = false;
          this.location = data.location.name;
          this.temperature = data.current.temp_c;
          this.description = data.current.condition.text;
          this.resetSearchQuery();
        })
        .catch()
      },
      resetSearchQuery(){
        this.searchQuery = '';
      }
    }
  }
</script>

