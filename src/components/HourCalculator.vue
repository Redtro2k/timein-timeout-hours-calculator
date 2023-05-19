<template>
    <div>
      <h1>Time In, Time Out Calculator</h1>
      <input type="time" v-model="timein">
      <input type="time" v-model="timeout">
      <button type="submit" @click="reset()">Reset</button>
      <button type="submit" @click="getHours()">Compute</button>
      <button type="submit" @click="arr.pop()">Remove One</button>
      <br>
      <h2>Week</h2>
      <ul>
        <li v-for="h in arr" :key="h">Hours: {{ h }}</li>
      </ul>
      <p>Final Total: {{ finaltotal }}</p>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue';
  import moment from 'moment';
  
  const timein = ref('');
  const timeout = ref('');
  const total = ref(0);
  const arr = ref([]);
  
  const finaltotal = computed(() =>
    arr.value.reduce((accumulator, currentValue) => accumulator + currentValue, 0)
  );
  
  function getHours() {
    const timeFormat = 'HH:mm';
    const timeInMoment = moment(timein.value, timeFormat);
    const timeOutMoment = moment(timeout.value, timeFormat);
    const duration = moment.duration(timeOutMoment.diff(timeInMoment));
    const hoursDiff = duration.asHours();
    total.value = hoursDiff.toFixed(2);
    arr.value.push(parseFloat(total.value));
  }
  
  function reset() {
    timeout.value = '';
    timein.value = '';
    total.value = 0;
  }
  </script>
  