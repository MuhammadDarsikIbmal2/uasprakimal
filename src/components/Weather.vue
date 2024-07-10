<template>
  <div class="weather-widget p-4 bg-light rounded shadow">
    <h2 class="widget-title mb-4">Widget Cuaca</h2>
    <div class="input-group mb-3">
      <input
        type="text"
        class="form-control"
        v-model="location"
        placeholder="Masukkan Lokasi"
      />
      <div class="input-group-append">
        <button class="btn btn-primary" type="button" @click="fetchWeatherData">
          Cari
        </button>
      </div>
    </div>
    <div v-if="weatherData" class="weather-data">
      <p class="location mb-2">Lokasi: {{ weatherData.name }}</p>
      <p v-if="weatherData.main" class="temperature">
        Temperatur: {{ Math.round(weatherData.main.temp - 273.15) }}°C
      </p>
      <p v-if="weatherData.weather" class="description mb-0">
        Deskripsi: {{ weatherData.weather[0].description }}
      </p>
    </div>
    <p v-else class="loader">Loading data...</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      location: "",
      weatherData: null,
    };
  },
  methods: {
    async fetchWeatherData() {
      try {
        const apiKey = "7a48709816b3cbf09fd45bec006fc903";
        const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${this.location}&appid=${apiKey}`;

        const response = await fetch(apiUrl);
        const data = await response.json();

        this.weatherData = data;
      } catch (error) {
        console.error("Error fetching weather data:", error);
      }
    },
  },
};
</script>

<style scoped>
.weather-widget {
  max-width: 400px;
  margin: 0 auto;
  margin-top: 50px;
}

.widget-title {
  font-size: 24px;
  text-align: center;
}

.weather-data {
  text-align: center;
}

.location {
  font-size: 18px;
  font-weight: bold;
}

.temperature {
  font-size: 24px;
  color: #ff5722;
}

.description {
  font-size: 16px;
}

.loader {
  font-size: 16px;
  text-align: center;
}
</style>
