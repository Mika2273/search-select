<script setup>
import SearchSelect from './components/SearchSelect.vue';
</script>

<template>
  <div class="container">
    <h1>Search Select</h1>
    <SearchSelect
      :options="[
        { name: 'USA', value: '1' },
        { name: 'Canada', value: '2' },
        { name: 'France', value: '3' },
        { name: 'Japan', value: '4' },
        { name: 'Italy', value: '5' },
        { name: 'India', value: '6' },
        { name: 'Spain', value: '8' },
        { name: 'UK', value: '9' },
        { name: 'China', value: '10' },
        { name: 'Australia', value: '11' },
        { name: 'Brazil', value: '12' },
        { name: 'Mexico', value: '13' },
        { name: 'Russia', value: '14' },
        { name: 'South Africa', value: '15' },
        { name: 'South Korea', value: '16' },
        { name: 'Sweden', value: '17' },
        { name: 'Switzerland', value: '18' },
        { name: 'Netherlands', value: '19' },
        { name: 'New Zealand', value: '20' },
        { name: 'Norway', value: '35' },
        { name: 'Denmark', value: '36' },
        { name: 'Finland', value: '37' },
        { name: 'Portugal', value: '38' },
        { name: 'Greece', value: '39' },
        { name: 'Turkey', value: '40' },
      ]"
    />
  </div>
</template>
