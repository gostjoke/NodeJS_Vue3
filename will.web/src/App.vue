<script setup lang="ts">
</script>

<template>
    
    
  <ul>
    <li><router-link to="/">home</router-link></li>
    <li><router-link to="/login">login</router-link></li>
    <li><a href="contact.asp">Contact</a></li>
    <li><a href="about.asp">About</a></li>
  </ul>
    <router-view></router-view>
</template>

<style scoped>
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  width: 5%;
  background-color: #f1f1f1;
  height: 100%; /* Full height */
  position: fixed; /* Make it stick, even on scroll */
  overflow: auto; /* Enable scrolling if the sidenav has too much content */
}
</style>
