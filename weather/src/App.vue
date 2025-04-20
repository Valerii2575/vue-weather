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
  <div class="weather">
    <div class="container">
      <div class="card weather-form">
        <input type="text" class="weather-form_input"
              placeholder="Enter city">
              <button class="weather-form_btn">Search</button>
      </div>

      <div class="card weather-load">
        Loader....
      </div>

      <div class="weather-info">
        <div class="weather-info_text">
          <p class="card">Phuken</p>
          <p class="card">29C</p>
          <p class="card">Sunny</p>
        </div>
      </div>
    </div>

    <div class="weather-bg">
      <div>
        <img class="weather-bg_img bg" src="./assets/sunny-sky.jpg" alt="">
        <img class="weather-bg_img sunny-sky" src="./assets/sunny-sky.jpg" alt="">
        <img class="weather-bg overcast" src="./assets/overcast.jpg" alt="">
        <img class="weather-bg partly-cloudy" src="./assets/partly-cloudy.jpg" alt="">
      </div>
    </div>

  </div>
</template>
<script setup>

</script>

