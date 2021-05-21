<template>
<div class="container">
  <div class="weather-icon">
    <div class="weather-icons">
      
    </div>
    <div class="row">
      <input type="text" class=" col-9 form-control">
      <button @click="weatherApi()" class="btn btn-success col-2 btn-search">Поиск</button>
    </div>
  </div>
</div>
</template>
<script>
import Weather from '@/components/Weather.vue';
export default {
  name: 'App',
  data: () => ({
    arr: [

    ]
  }),
  
  methods: {
    weatherApi() {
      let token = '1cd30991dd9bd85fa384b9abc5096a2b'
      let input = document.querySelector('input')
      fetch(`api.openweathermap.org/data/2.5/weather?q=${input.value}&appid=${token}`)
      .then(res => res.json())
      .then(json => {
      console.log(json);
      let z = {
        city: json
      }
      this.arr.unshift(z)
          
    })
    } 
  },
  mounted: function() {
      // this.$nextTick(function () {
      //   const successCallBlock = (position) => {
      //   console.log(position);
      // }
      // navigator.geolocation.watchPosition(successCallBlock)
      // })
      // if ('geolocation' in navigator) {
      //   console.log('geolocation avaiable');
      //   navigator.geolocation.watchPosition( position => {
      //     console.log(position);
      //   } )
      // } else {
      //   console.log('geolocation ');
      // }
      if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(function(position) {
      }
      )}
  // mounted: function () {
  //     let token = '1cd30991dd9bd85fa384b9abc5096a2b'
  //     let input = document.querySelector('input')
  //     fetch(`api.openweathermap.org/data/2.5/weather?q=${input.value}&appid=${token}`)
  //     .then(res => res.json())
  //     .then(json => {
  //     console.log(json);
  //     let z = {
  //       city: json
  //     }
  //     this.arr.unshift(z)
          
  //   })
  // },
}}
</script>

<style scopped>
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
}

.rain{
  background-color: #41ba9c;
  height: 170px;
  width: 180px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.x2 {
	-webkit-transform: scale(0.3);
	-moz-transform: scale(0.3);
	transform: scale(0.3);
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
} */
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

