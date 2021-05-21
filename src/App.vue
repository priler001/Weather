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
  components: {
    Weather
  }
//   methods: {
//     weatherApi() {
//       let token = '1cd30991dd9bd85fa384b9abc5096a2b'
//       let input = document.querySelector('input')
//       fetch(`api.openweathermap.org/data/2.5/weather?q=${input.value}&appid=${token}`)
//       .then(res => res.json())
//       .then(json => {
//       console.log(json);
//       let z = {
//         city: json
//       }
//       this.arr.unshift(z)
          
//     })
//     } 
//   },
//   mounted: function() {
//       // this.$nextTick(function () {
//       //   const successCallBlock = (position) => {
//       //   console.log(position);
//       // }
//       // navigator.geolocation.watchPosition(successCallBlock)
//       // })
//       // if ('geolocation' in navigator) {
//       //   console.log('geolocation avaiable');
//       //   navigator.geolocation.watchPosition( position => {
//       //     console.log(position);
//       //   } )
//       // } else {
//       //   console.log('geolocation ');
//       // }
//       if (navigator.geolocation) {
//     navigator.geolocation.getCurrentPosition(function(position) {
// }
//       )}
//   // mounted: function () {
//   //     let token = '1cd30991dd9bd85fa384b9abc5096a2b'
//   //     let input = document.querySelector('input')
//   //     fetch(`api.openweathermap.org/data/2.5/weather?q=${input.value}&appid=${token}`)
//   //     .then(res => res.json())
//   //     .then(json => {
//   //     console.log(json);
//   //     let z = {
//   //       city: json
//   //     }
//   //     this.arr.unshift(z)
          
//   //   })
//   // },
// }}
}
</script>

<style scopped>
</style>
