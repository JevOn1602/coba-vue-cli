<template>
  <header>
    <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
    <h2>Mobile Legend : Bang Bang</h2>
    <button @click="$emit('ganti-hero')">Pilih Hero Random</button>
    <slot name="heroRand"></slot>
  </header>
</template>
<script>
export default {
  name: "Header",
};
</script>
<style></style>
