<template>
  <div id="app" class="bg-dark">
    <AppNavbar />
    <div class="container">
      <iframe 
        src="https://store.steampowered.com/widget/1737640/" 
        frameborder="0" 
        width="646" 
        height="190">
      </iframe>
    </div>
  </div>
</template>

<script>
import AppNavbar from './components/AppNavbar.vue'

export default {
  name: 'App',
  components: {
    AppNavbar
  }
}
</script>

<style>
@import "~bootstrap/dist/css/bootstrap.min.css";
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
}
.bg-dark {
  background-color: #343a40;
}
</style>
