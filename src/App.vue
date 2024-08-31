<template>
  <div id="app" class="bg-dark d-flex flex-column min-vh-100">
    <AppNavbar />
    <main class="flex-fill">
      <div class="container my-5">
        <div class="embed-responsive embed-responsive-16by9 steam-widget-container">
          <iframe 
            src="https://store.steampowered.com/widget/1737640/" 
            frameborder="0" 
            allowfullscreen>
          </iframe>
        </div>
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

/* Адаптация iframe для Steam виджета */
.steam-widget-container {
  position: relative;
  width: 100%;
  height: 0;
  padding-bottom: 29.41%; /* Соотношение сторон 646x190 = 29.41% */
}

.steam-widget-container iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: 0;
}

/* Настройки контейнера под разные устройства */
@media (max-width: 768px) {
  .steam-widget-container {
    padding-bottom: 50%; /* Изменяем соотношение сторон под мобильные устройства */
  }
}

@media (max-width: 576px) {
  .steam-widget-container {
    padding-bottom: 75%; /* Еще большее изменение для маленьких экранов */
  }
}
</style>
