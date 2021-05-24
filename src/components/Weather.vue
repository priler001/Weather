<template>
    <div class="content">
      <h1 class="text-center pt-5">Прогноз погоды</h1>
      <div class="weather-icons">
      
    </div>    
    <div class="row">
      <input type="text" class="form-control mt-4" placeholder="Введите страну">
      <button @click="weatherApi()" class="btn-search mt-4">Найти</button>
      <div class="info">
        <h3 class="mt-3 text-center" v-for="(y, r) in arr" :key="r">{{y.name}}</h3>
        <h4 class="text-center"  v-for="(y, r) in arr" :key="r">{{y.main}}</h4>
        <h2 class="temp text-center" v-for="(y, r) in arr" :key="r">{{y.temp}}</h2>
        <div class="x2 text-center">
          <div class="cloud"></div>
        </div>
      </div>
    </div>
    </div>
</template>
<script>
export default {
  props: ['reports'],
  name: 'App',
  data: () => ({
    arr : [

    ]
  }),
  
  methods: {
    weatherApi() {
      let token = '1cd30991dd9bd85fa384b9abc5096a2b'
      let input = document.querySelector('input')
      fetch(`https://api.openweathermap.org/data/2.5/weather?q=${input.value}&appid=${token}&units=metric`)
      .then(res => res.json())
      .then(json => {
        console.log(json);
        let h3 = document.querySelector('h3')
        let h4 = document.querySelector('h4')
        let h2 = document.querySelector('h2')
        h3.innerHTML = json['name']
        h4.innerHTML = json['main']['temp']
        h2.innerHTML = json['weather'][0]['main']
      })
    }
},
mounted: function() {
    console.log("getLocation Called");
    var cityApi = 'https://api.bigdatacloud.net/data/reverse-geocode-client' 
      navigator.geolocation.getCurrentPosition(
      (position) => {
      cityApi =
      cityApi +
      "?latitude=" +
      position.coords.latitude +
      "&longitude=" +
      position.coords.longitude +
      "&localityLanguage=en"
      fetch(cityApi)
      .then(res => res.json())
      .then(json => {
      let cityn = json['city']
      let z = {
        city: cityn,
      }
      this.arr.unshift(z)
      fetch(`https://api.openweathermap.org/data/2.5/weather?q=${cityn}&appid=1cd30991dd9bd85fa384b9abc5096a2b&units=metric`)
        .then(res => res.json())
        .then(json => {
          console.log(json);
          let weatherInfo = {
            name: json['name'],
            temp: json['main']['temp'],
            main: json['weather'][0]['main'],
            tempmax: json['main']['temp_max'],
            tempmin: json['main']['temp_min'],
            feelslike: json['main']['feels_like']
          }
          this.arr.unshift(weatherInfo)
        })
        
      })
    },)
},
}
</script>

<style scopped>
@import url('https://fonts.googleapis.com/css2?family=KoHo:wght@500&display=swap');
body{
  font-family: 'KoHo', sans-serif !important;
}
.row{
  display: flex !important;
  justify-content: space-between;
  margin-top: 100px;
}
.btn-search{
  width: 200px !important;
  background-color: #fff;
  color: #000;
  border: 1px solid #000;
  border-radius: 5px;
  transition: .5s;
}

.btn-search:hover{
  background-color: rgb(56, 22, 59);
  border-radius: 50px;
  color: #fff;
}

.form-control{
  width: 1100px !important;
}

.temp{
  font-size: 50px !important;
  font-weight: bold;
}
@media (max-width: 1400px) {
  .container{
    width: 1200px !important;
  }
  .btn-search{
    margin-top: 30px !important;
    width: 100% !important;
    height: 40px;
  }
  input{
    width: 100% !important;
  }
    .x2 {
	-webkit-transform: scale(0.3);
	-moz-transform: scale(0.3);
	transform: scale(0.3);
  margin-right: -242px !important;

}
}
@media (max-width: 1000px) {
  .container{
    width: 950px !important;
  }
  .btn-search{
    margin-top: 30px !important;
    width: 100% !important;
  }
    .x2 {
	-webkit-transform: scale(0.3);
	-moz-transform: scale(0.3);
	transform: scale(0.3);
  margin-right: -150px !important;

}
}
@media (max-width: 900px) {
  .container{
    width: 850px !important;
  }
  .btn-search{
    margin-top: 30px !important;
    width: 100% !important;
  }
    .x2 {
	-webkit-transform: scale(0.3);
	-moz-transform: scale(0.3);
	transform: scale(0.3);
  margin-right: -150px !important;

}
}
@media (max-width: 800px) {
  .container{
    width: 750px !important;
  }
  .btn-search{
    margin-top: 30px !important;
    width: 100% !important;
  }
  .x2 {
	-webkit-transform: scale(0.3);
	-moz-transform: scale(0.3);
	transform: scale(0.3);
  margin-left: 0px !important;

}
}
@media (max-width: 700px) {
  .container{
    width: 650px !important;
  }
  .btn-search{
    margin-top: 30px !important;
    width: 100% !important;
  }
  .x2 {
	-webkit-transform: scale(0.3);
	-moz-transform: scale(0.3);
	transform: scale(0.3);
  margin-left: 0px !important;
}
}
@media (max-width: 400px) {
  .container{
    width: 350px !important;
  }
  .btn-search{
    margin-top: 30px !important;
    width: 100% !important;
  }
  .x2 {
	-webkit-transform: scale(0.3);
	-moz-transform: scale(0.3);
	transform: scale(0.3);
  margin-left: 0px !important;

}
}
@media (max-width: 300px) {
  .container{
    width: 0px !important;
  }
  .btn-search{
    margin-top: 30px !important;
    width: 100px !important;
  }
  .x2 {
	-webkit-transform: scale(0.3);
	-moz-transform: scale(0.3);
	transform: scale(0.3);
  margin-left: 0px !important;

}
}


/* NIGHT */
/* .night{
  background-color: rgb(37, 36, 36);
  height: 170px;
  width: 180px;
  display: flex;
  align-content: center;
  justify-content: center;
  border-radius: 2px;
}

.night div{
  animation-name: night;
  animation-duration: 4s;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
  width: 100px;
  height: 110px;
  border-radius: 100%;
  background-color:transparent;
  box-shadow: -23px 0 0px -10px #fff;
  margin-right: -65px;
  margin-top: 5px;
}

@keyframes night{
  0%{
    transform: rotate(-30deg);
  }
  25%{
    transform: translateY(5px);
    transform: rotate(-30deg);
  }
  50%{
    transform: translateY(10px);
  }
  100%{
    transform: translateY(0px);
    transform: rotate(-30deg);
  }
}

.sunny{
  background-color: #4fc1e9;
  height: 170px;
  width: 180px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.sunny div{
  animation-name: sunny;
  animation-duration: 4s;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
  width: 90px;
  height: 90px;
  border-radius: 100%;
  background-color: #ffe400;
  box-shadow: rgb(255 255 0 / 10%) 0 0 5px 5px;
}
@keyframes sunny{
  0%{
    transform: translateY(0px);
  }
  25%{
    transform: translateY(-8px);
  }
  50%{
    transform: translateY(8px);
  }
  100%{
    transform: translateY(-0px);
  }
} */


.x2 {
	-webkit-transform: scale(0.3);
	-moz-transform: scale(0.3);
	transform: scale(0.3);
  margin-right: -400px;
}
.cloud {
	background: #ccc;
	background: -moz-linear-gradient(top,  #fff 5%, #f1f1f1 100%);
	background: -webkit-gradient(linear, left top, left bottom, color-stop(5%,#fff), color-stop(100%,#f1f1f1));
	background: -webkit-linear-gradient(top,  #fff 5%,#f1f1f1 100%);
	background: -o-linear-gradient(top,  #fff 5%,#f1f1f1 100%);
	background: -ms-linear-gradient(top,  #fff 5%,#f1f1f1 100%);
	background: linear-gradient(top,  #fff 5%,#f1f1f1 100%);
	filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#fff', endColorstr='#f1f1f1',GradientType=0 );
	
	-webkit-border-radius: 100px;
	-moz-border-radius: 100px;
	border-radius: 100px;
	
	-webkit-box-shadow: 0 8px 5px rgba(0, 0, 0, 0.1);
	-moz-box-shadow: 0 8px 5px rgba(0, 0, 0, 0.1);
	box-shadow: 0 8px 5px rgba(0, 0, 0, 0.1);

	height: 120px;
	position: relative;
	width: 350px;
}

.cloud:after, .cloud:before {
  background: #ccc;
	content: '';
	position: absolute;
	z-indeX: -1;
}

.cloud:after {
	-webkit-border-radius: 100px;
	-moz-border-radius: 100px;
	border-radius: 100px;

	height: 100px;
	left: 50px;
	top: -50px;
	width: 100px;
}

.cloud:before {
	-webkit-border-radius: 200px;
	-moz-border-radius: 200px;
	border-radius: 200px;

	width: 180px;
	height: 180px;
	right: 50px;
	top: -90px;
}

.cloud span{
  width: 1px;
  height: 6px;

  animation: rain 0.65s linear infinite;
}
/* .drop {
  background-color: red;
  width: 5px;
  height: 89px;
  position: absolute;
  animation: fall .63s linear infinite;
  animation-name: fall;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

/* animate the drops*/

</style>

