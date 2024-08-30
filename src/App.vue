<template>
  <div id="app" class="bg-dark d-flex flex-column min-vh-100">
    <AppNavbar />
    <main class="flex-fill">
      <div class="container my-5">
        <iframe 
          src="https://store.steampowered.com/widget/1737640/" 
          frameborder="0" 
          width="646" 
          height="190">
        </iframe>
      </div>
    </main>
    <footer class="site-footer text-center py-4">
      <p class="text-white mb-0">
        &copy; {{ currentYear }} Stylua Games.<br />
        Создано с любовью и преданностью к играм.
      </p>
    </footer>
  </div>
</template>

<script>
import AppNavbar from './components/AppNavbar.vue'

export default {
  name: 'App',
  components: {
    AppNavbar
  },
  data() {
    return {
      currentYear: new Date().getFullYear()
    };
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

/* Основной контейнер занимает всю высоту экрана */
.d-flex {
  display: flex;
}

/* Футер */
.site-footer {
  background-color: #222; /* Цвет фона для футера */
  padding: 1rem;
}

.site-footer p {
  margin: 0;
  font-size: 0.875rem;
}

/* Прокрутка страницы в случае необходимости */
html, body {
  height: 100%;
}
</style>
