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
        { name: 'Germany', value: '7' },
        { name: 'Spain', value: '8' },
        { name: 'UK', value: '9' },
        { name: 'China', value: '10' },
      ]"
    />
  </div>
</template>
