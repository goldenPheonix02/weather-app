<template lang="">
  <div class="container">
    <Input @submitted="OnSubmit" />
    <div class="date">
      <p class="name">{{ city }}</p>
      <p class="day">{{ date }}</p>
    </div>
    <div class="temp">
      <p>{{ temp }} <sup>o</sup> C</p>
    </div>
    <div class="clouds">
      <p>{{ clouds }}</p>
    </div>
  </div>
</template>
<script>
import Input from "@/components/input.vue";
const https = require("https");
const keys = require("../assets/API_KEY.json");
const date = require("../assets/date.js");

export default {
  name: "DataCard",
  components: {
    Input,
  },
  data() {
    return {
      date: date.getDate(),
      time: "23:45 PM",
      temp: "27",
      city: "",
      clouds: "Clouds",
    };
  },
  methods: {
    OnSubmit(name) {
      console.log(name);
      const API_key = keys["key"];
      https.get(
        "https://api.openweathermap.org/data/2.5/weather?q=" +
          name +
          "&units=metric&appid=" +
          API_key,
        (res) => {
          console.log(res.statusCode);
          let data = "";
          res.on("data", (chunk) => {
            // Data is being received in chunks, we add it to the data variable to save it
            data += chunk;
          });
          res.on("end", () => {
            // all data has been received, now we can parse it and are done
            var parsedData = JSON.parse(data);
            if (res.statusCode === 404) {
              alert("City Not Found");
            } else {
              this.clouds = parsedData.weather[0].description;
              this.temp = parsedData.main.temp;
              this.city = parsedData.name;
            }
          });
        }
      );
    },
  },
};
</script>
<style scoped>
.container {
  text-align: center;
  display: inline-block;
  padding: 1rem 5rem 10rem;
  border-radius: 5px;
  margin: 30px auto 18px;
}
@media screen {
}
.date {
  margin: 40px 0 0;
}
.name {
  font-size: 1.5rem;
  font-weight: 700;
}
.day {
  font-size: 2rem;
}
.time,
.clouds {
  font-size: 1.2rem;
  word-spacing: 3px;
}
p:nth-child(1) {
  line-height: 2;
}
.temp {
  position: relative;
  margin: 0px auto;
  font-size: 3.8rem;
}
</style>
