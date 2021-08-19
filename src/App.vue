<template>
  <!--<img alt="Vue logo" src="./assets/logo.png" />-->
  <!--<HelloWorld msg="Hello Vue 3 + Vite" />-->
  <!--<KeyPad />-->
  <!--<RebirthLuggage />-->
  <RebirthLuggageImages />
</template>

<script setup>
//import HelloWorld from './components/HelloWorld.vue'
import KeyPad from './components/KeyPad.vue'
import RebirthLuggage from './components/RebirthLuggage.vue'
import RebirthLuggageImages from './components/RebirthLuggageImages.vue'

// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md
</script>

<style>
#app {
  font-family: "ModernWarfare", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /*margin-top: 60px;*/
}

@font-face {
  font-family: "ModernWarfare";
  src: local("ModernWarfare"),
   url(./fonts/ModernWarfare-8MM6z.ttf) format("truetype");
}
</style>
