<template>
  
  <div id="app">
    <main>
      <div class="search-box">
        <input type="text"  class="search-bar" placeholder="Search..." v-model="query" @keypress="fetchWeather" />
        
      </div>
    
  

  <div class="weather-wrap">
    <div class="location-box">
      <div class="location">London, UK</div>
      <div class="date">Monday 20 August2020</div> 
    </div>
    
    
    <div class="weather-box">
      <div class="temp">{{ Math.round(weather.main.temp) }}</div> 
        <div class="weather">{{ weather.weather[0].main }}</div> 
    </div>
  </div>
    </main>
  </div>
</template>
 
<script>


export default {
  name: 'App',
  
  data() {
    return {
      api_key: '0a8e81f8c1472f6579f1c58aff899d65',
      url_base: 'https://home.openweathermap.org/data/2.5',
      query:'',
      weather: {}
    }
  },  
  methods: {
    fetchWeather (e) {
      if(e.key == "Enter" ) {
        fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID = ${this.api_key}`)
          .then(res => {
            return res.json();
          }).then(this.setResults);
      }
    },

    setResults (results) {
      this.weather = results;
    }

  }

}

</script>

<style>
 * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
 }

 body {
   font-family: 'Times New Roman', Times, serif;
   font-display: left;
   font-size: 5px;
 }


#app{
  background-image: url('./assets/mountain.jpg');
  background-size: cover;
  background-position: bottom;
  transition-duration: 0.4s;
}

main {

min-height: 120vh;
padding: 30px;

background-image: linear-gradient(to bottom, rgb(167, 177, 179), rgba(46, 98, 140, 0.75));
}

.search-box {

  width: 100px;
  margin-bottom: 30px;
  
}

.search-box .search-bar {

  display: block;
  width: 30cm;
  padding: 20px;
  font-size: 20px;
  color: black;

  appearance: none;
  border: none;
  outline: none;
  background: none;

  box-shadow: 0px 0px 0px 10px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.842);
  border-radius: 0px 16px 8px 0px;
  transition: 0.4s;

}

.search-box .search-bar :focus {

  background-color: rgba(255,255,255,0.75);
  box-shadow: 0px 0px 0px 3px;
  border-radius: 10px 0px 0px 10px;
}



.location-box .location {

  color: antiquewhite;
  font-size: 60px;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.location-box .date {
  color: white;
  font-size: 40px;
  text-align: center;
  font-style: italic;
}

.weather-box {
  text-align: center;
}


.weather-box .temp {
  display: inline-block;
  padding: 10px 25px;
  color: white;
  font-size: 58px;
  font-weight: 900;
  text-align: center;
 
  /* text-shadow: 3px 6px rgba(0, 0, 0, 0.75); */
  background-color: 5px 5px rgba(255, 255, 255, 0.25);
  
}

.weather-box .weather {
  text-align: center;
  font-size: 48px;
  color: white;
  font-weight: 500;
  font-style: italic;

  text-shadow: 3px 6px rgba(224, 210, 210, 0.25);



}

  
</style>
