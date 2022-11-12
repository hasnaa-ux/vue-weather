<template>
  <div class="search-box">
    <input
      id="country"
      type="text"
      name="country"
      v-model="query"
      placeholder="Search..."
      @keypress="featchWeather"
    />
  </div>

  <div class="weather-wrap" v-if="typeof weather.main != 'undefiend'">
    <!-- there is an error here-->
    <div class="location-box">
      <div class="location">{{ weather.name }} {{ weather.sys.country }}</div>
      <div class="date">Monday 20 January 2020</div>
    </div>

    <div class="weather-box">
      <div class="temp">9 c</div>
      <div class="weather">Rain</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      api_key: "893e4e2c9ea095ec2eeb47515bcfb300",
      query: "",
      url_base: "https://api.openweathermap.org/",
      weather: {},
    };
  },
  methods: {
    featchWeather(e) {
      if (e.key == "Enter") {
        fetch(
          `${this.url_base}Weather?q= ${this.query}&units=metric&APPID = ${this.api_key}`
        )
          .then((res) => {
            return res.json();
          })
          .then(this.setResult);
      }
    },
    setResult(Results) {
      this.weather = Results;
    },
  },
};
</script>

<style scoped>
.search-box {
  width: 100%;
  display: block;
  margin-bottom: 30px;
}
input {
  display: block;
  border: none;
  width: 288px;
  height: 40px;
  border-radius: 0 16px 0 16px;
  padding: 5px;
  color: #313131;
  outline: none;
  background: none;
  appearance: none;
  background-color: rgba(255, 255, 255, 0.6);
  transition: 0.4s;
  padding-left: 15px;
}
input:focus {
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 16px 0 16px 0;
}
.location-box .location {
  color: #fff;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}
.location-box .date {
  color: #fff;
  font-size: 20px;
  font-weight: 300;
  text-align: center;
  font-style: italic;
}

.weather-box {
  text-align: center;
}
.weather-box .temp {
  color: #fff;
  padding: 10px 25px;
  font-size: 100px;
  font-weight: 900;
  display: inline-block;
  background-color: rgba(255, 255, 255, 0.25);
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  border-radius: 16px;
  margin: 30px 0;
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
.weather-box .weather {
  color: #fff;
  font-weight: 700;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  font-size: 48px;
  font-style: italic;
}
</style>
