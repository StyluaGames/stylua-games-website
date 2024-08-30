<template>
  <header>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container-xxl">
        <a class="navbar-brand" href="#">
          <img src="../assets/Stylua.png" alt="" width="195.68" height="79.68" />
        </a>
        <button 
          class="navbar-toggler" 
          type="button" 
          @click="isNavCollapsed = !isNavCollapsed" 
          aria-controls="navbarSupportedContent" 
          aria-expanded="false" 
          aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div :class="['collapse', 'navbar-collapse', { show: !isNavCollapsed }]" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#">Наши игры</a>
            </li>
            <!-- Показывать только те ссылки, которые не заблокированы -->
            <li class="nav-item" v-for="link in filteredLinks" :key="link.name">
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
      // Фильтруем ссылки в зависимости от региона
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
.navbar-brand img {
  width: 195.68px;
  height: 79.68px;
}
</style>
