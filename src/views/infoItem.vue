<template>
  <div class="w-[650px] h-[500px] bg-[rgb(211,211,211,.5)] rounded-lg">
    <h1 class="text-center mt-5 text-2xl font-medium">
      This data
      <span class="text-[rgb(0,0,255)]">
        {{ info.forecast.forecastday[0].date }}
      </span>
    </h1>
    <div class="flex justify-between px-5 mt-5">
      <h2>the temperature</h2>
      <h2 class="text-center">
        max {{ info.forecast.forecastday[0].day.maxtemp_c }}° /
        {{ info.forecast.forecastday[0].day.mintemp_c }}° min
      </h2>
      <h2>in {{ info.location.name }} today</h2>
    </div>
    <div class="text-center mt-10">
        <h1 class="text-2xl font-medium">Information for the next 3 days</h1>
        <div class="flex justify-between px-5 mt-5">
      <div class="w-32 h-20 rounded-lg bg-[rgb(211,211,211)] text-center py-4">
        {{ info.forecast.forecastday[0].date }}
        <h3>
          {{ info.forecast.forecastday[0].day.maxtemp_c }}° /
          {{ info.forecast.forecastday[0].day.mintemp_c }}°
        </h3>
      </div>
      <div class="w-32 h-20 rounded-lg bg-[rgb(211,211,211)] text-center py-4">
        {{ info.forecast.forecastday[1].date }}
        <h3>
          {{ info.forecast.forecastday[1].day.maxtemp_c }}° /
          {{ info.forecast.forecastday[1].day.mintemp_c }}°
        </h3>
      </div>
      <div class="w-32 h-20 rounded-lg bg-[rgb(211,211,211)] text-center py-4">
        {{ info.forecast.forecastday[2].date }}
        <h3>
          {{ info.forecast.forecastday[2].day.maxtemp_c }}° /
          {{ info.forecast.forecastday[2].day.mintemp_c }}°
        </h3>
      </div>
    </div>

    </div>
  </div>
</template>

<script>
export default {
  props: {
    info: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style></style>
