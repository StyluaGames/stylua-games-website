<template>
  <header>
    <nav class="navbar navbar-expand-lg navbar-dark bg-gray-800 shadow-lg">
      <div class="container-xxl">
        <a class="navbar-brand" href="#">
          <img src="../assets/Stylua.png" alt="" class="w-48 h-auto animate__animated animate__fadeIn" />
        </a>
        <button 
          class="navbar-toggler text-white"
          type="button" 
          @click="isNavCollapsed = !isNavCollapsed" 
          aria-controls="navbarSupportedContent" 
          aria-expanded="false" 
          aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div :class="['collapse', 'navbar-collapse', { show: !isNavCollapsed }]" id="navbarSupportedContent">
          <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link active text-white" aria-current="page" href="#">Наши игры</a>
            </li>
            <!-- Показывать только те ссылки, которые не заблокированы -->
            <li v-for="link in filteredLinks" :key="link.name" class="nav-item" :class="{ 'animate__animated': !link.blocked, 'animate__fadeIn': !link.blocked, 'animate__delay-1s': !link.blocked }">
              <a v-if="!link.blocked" class="nav-link" :href="link.url">
                {{ link.name }}
              </a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'AppNavbar',
  data() {
    return {
      isNavCollapsed: true,
      region: null,
      links: [
        { name: 'Мы в YouTube', url: 'https://www.youtube.com/@styluagames', blocked: false },
        { name: 'Мы в TikTok', url: 'https://www.tiktok.com/@styluagames', blocked: false },
        { name: 'Мы в Instagram', url: 'https://www.instagram.com/styluagames', blocked: false },
        { name: 'Мы в X', url: 'https://twitter.com/StyluaGames', blocked: false },
        { name: 'Мы в Facebook', url: 'https://www.facebook.com/Stylua-Games-363567771448505', blocked: false },
        { name: 'Мы в ВК', url: 'https://vk.com/styluagames', blocked: false },
      ]
    };
  },
  computed: {
    filteredLinks() {
      if (this.region === 'Russia') {
        return this.links.map(link => {
          if (['Мы в TikTok', 'Мы в Instagram', 'Мы в X', 'Мы в Facebook'].includes(link.name)) {
            link.blocked = true;
          } else {
            link.blocked = false;
          }
          return link;
        });
      } else {
        return this.links.map(link => {
          if (link.name === 'Мы в ВК') {
            link.blocked = true;
          } else {
            link.blocked = false;
          }
          return link;
        });
      }
    }
  },
  created() {
    this.getUserRegion();
  },
  methods: {
    async getUserRegion() {
      try {
        // Получение IP-геолокации пользователя
        const response = await fetch(`https://api.ipgeolocation.io/ipgeo?apiKey=${process.env.VUE_APP_API_KEY}`);
        const data = await response.json();
        this.region = data.country_name; // Название страны
      } catch (error) {
        console.error('Ошибка при получении региона:', error);
        this.region = 'Rest of the world'; // Если ошибка, предполагаем, что это не Россия
      }
    }
  }
};
</script>

<style scoped>
@import "~bootstrap/dist/css/bootstrap.min.css";
@import "~animate.css/animate.min.css"; /* Подключение Animate.css */

.navbar-brand img {
  width: 150px; /* Размер изображения можно скорректировать */
  height: auto;
}

.navbar {
  background: linear-gradient(135deg, #1f1f1f, #333); /* Градиент фона для современного вида */
}

.navbar-toggler {
  border: none;
  background-color: transparent;
}

.nav-link {
  font-size: 1rem; /* размер шрифта */
  margin-left: 1rem;
  transition: color 0.3s ease;
}

.nav-link:hover {
  color: #f8f9fa;
}

.nav-item {
  opacity: 0;
  animation: fadeInUp 1s forwards; /* Анимация появления элементов */
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Анимации переходов */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s ease;
}
.fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
  opacity: 0;
}
</style>
