<script setup>
// TODO: dev gql
// TODO: language-packs
// https://quasar.dev/options/quasar-language-packs
// TODO: remember
// TODO: tx
// https://testing.quasar.dev/
</script>

<template>
  <router-view />
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto+Slab&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Onest:wght@100..900&display=swap');

button,
input {
  font-family: "Onest", sans-serif;
  font-optical-sizing: auto;
  font-weight: 300;
  font-style: normal;
  text-transform: uppercase;
}

.info-text {
  font-family: "Onest", sans-serif;
  font-optical-sizing: auto;
  font-weight: 500;
  font-style: normal;
  font-size: 16px;
}

h2 {
  font-family: 'Roboto Slab', serif;
  font-size: 20px;
  font-weight: normal;
  margin-bottom: 1vh
}

p {
  font-family: 'Roboto Slab', serif;
  font-size: 15px;
  font-weight: normal;
  margin-bottom: 0.5vh;
  line-height: 20px;
}

a {
  color: #ac5de7;
  text-decoration: none;
}

p,
li {
  margin-bottom: 10px;
}

ul {
  list-style: none;
}

img {
  max-width: 100%
}

.raw_txt {
  white-space: pre-line;
  word-wrap: break-word;
}
</style>
