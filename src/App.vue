<template>
  <Header />
</template>

<script setup>
import Header from "./components/Header.vue";
</script>

<style>
@font-face {
  font-family: "Tele2";
  src: url("~@/assets/fonts/tele2_textsans_regular.woff") format("woff");
  font-weight: 400;
  font-style: normal;
}

@font-face {
  font-family: "Tele2";
  src: url("~@/assets/fonts/tele2_textsans_bold.woff") format("woff");
  font-weight: 700;
  font-style: normal;
}
body {
  width: 100%;
  min-width: 375px;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Tele2", sans-serif;
}
</style>
