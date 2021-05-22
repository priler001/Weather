<template>
<div class="background">
  <div class="container">
        <Weather  @cityname="addArr" :reports="arr" />
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
  },
  methods: {
    // addArr(value) {
    //   console.log(value);
    //   this.arr.unshift(value)
    // }
  }
}
</script>

<style scopped>
.background{
  width: 100%;
  height: 100vh;
  background-color: rgb(157, 78, 231);
  color: #fff;
}
</style>
