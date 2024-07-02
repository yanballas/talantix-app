<script setup>
defineProps({
  msg: String,
});
</script>

<template>
  <h1>{{ msg }}</h1>
</template>

<style scoped>
  h1 {
    font-size: 48px;
    color: #fff;
  }
</style>
