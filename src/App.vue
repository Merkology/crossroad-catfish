<template>
  <!--
  <nav>
    <router-link to="/">Home</router-link> |
  </nav>
-->
  <div class="w-full pb-14">
    <Navigation />
  </div>
  <router-view />
</template>

<script setup>
  import Navigation from "@/components/Navigation.vue"
</script>

<style>
  body{
    background-color: #F5EBDC;
  }
</style>
