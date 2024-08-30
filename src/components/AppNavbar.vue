<template>
  <header>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container-xxl">
        <a class="navbar-brand" href="#">
          <img src="../assets/Stylua.png" alt="" width="195,68" height="79,68" />
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
            <li class="nav-item" v-for="link in links" :key="link.name">
              <a class="nav-link" :href="link.url">{{ link.name }}</a>
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
      links: [
        { name: 'Мы в YouTube', url: '#' },
        { name: 'Мы в TikTok', url: '#' },
        { name: 'Мы в Instagram', url: '#' },
        { name: 'Мы в Twitter', url: '#' },
        { name: 'Мы в Facebook', url: '#' },
        { name: 'Мы в ВК', url: '#' },
      ]
    };
  }
};
</script>

<style scoped>
.navbar-brand img {
  width: 195.68px;
  height: 79.68px;
}
</style>
