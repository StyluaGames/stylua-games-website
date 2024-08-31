<template>
  <div id="app">
    <AppNavbar />
    <main>
      <!-- Секция 1 с анимацией при скролле -->
      <section class="scroll-animation-section" ref="scrollSection1">
        <div class="scroll-content" ref="scrollContent1">
          <h2 class="title">Добро пожаловать в Stylua</h2>
          <p class="description">
            Откройте для себя мир инди игр и технологий, где каждая игра — это уникальное приключение, полное креативности и инноваций.
          </p>
        </div>
      </section>

      <!-- Секция 2.1 с анимацией при скролле -->
      <section class="scroll-animation-section" ref="scrollSection2_1">
        <div class="scroll-content" ref="scrollContent2_1">
          <h2 class="title">Наши игры</h2>
          <p class="description">
            Мы создаем захватывающие и увлекательные игры. Наш первый проект — <strong>Theory of Poltaran</strong>.
          </p>
        </div>
      </section>

      <!-- Секция 2.2 с анимацией при скролле -->
      <section class="scroll-animation-section" ref="scrollSection2_2">
        <div class="scroll-content" ref="scrollContent2_2">
          <!-- Вставка картинок и описания игры -->
          <div class="game-details">
            <img src="./assets/image-game-1.jpg" alt="Theory of Poltaran" class="game-image" />
            <div class="game-description">
              <h3>Theory of Poltaran</h3>
              <p>
                В 2018 году. Ранним утром Дэниэл просыпается от неожиданного звонка. Его лучший друг Дмитрий просит собрать некие камни…
                Дэниэл — главный герой, который должен помочь своему другу найти камни, отправившись в опасное приключение, полное тайн и загадок.
              </p>
              <ul class="features-list">
                <li>Современная и красивая графика</li>
                <li>Два вида оружия: ближнего и дальнего боя</li>
                <li>Опасные противники, мимикрирующие под обычных людей</li>
                <li>Локации для прогулок и наслаждения окружающей средой</li>
                <li>Непредсказуемый сюжет, который удивит вас</li>
              </ul>
            </div>
          </div>
          <!-- Вставка виджета Steam -->
          <iframe 
            src="https://store.steampowered.com/widget/1737640/" 
            frameborder="0" 
            width="646" 
            height="190"
            class="steam-widget">
          </iframe>
        </div>
      </section>

      <!-- Секция 3 с анимацией при скролле -->
      <section class="scroll-animation-section" ref="scrollSection3">
        <div class="scroll-content" ref="scrollContent3">
          <h2 class="title">О нашей компании</h2>
          <p class="description">
            Stylua Games — это команда двух разработчиков, стремящихся к инновациям и креативности в каждом проекте. Мы начали наш путь в 2019 году, когда два новичка в разработке игр решили создать что-то уникальное. Мы верим в силу креативности и стремимся создать игры, которые увлекут и вдохновят наших игроков.
          </p>
        </div>
      </section>
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
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import AppNavbar from './components/AppNavbar.vue'

gsap.registerPlugin(ScrollTrigger);

export default {
  name: 'App',
  components: {
    AppNavbar
  },
  data() {
    return {
      currentYear: new Date().getFullYear()
    };
  },
  mounted() {
    this.initScrollAnimations();
  },
  methods: {
    initScrollAnimations() {
      // Анимация для секции 1
      gsap.fromTo(this.$refs.scrollContent1, 
        { y: 100, opacity: 0 }, 
        {
          y: 0, opacity: 1,
          scrollTrigger: {
            trigger: this.$refs.scrollSection1,
            start: "top 80%",
            end: "bottom top",
            scrub: true,
            toggleActions: "play reverse play reverse"
          }
        });

      // Анимация для секции 2.1
      gsap.fromTo(this.$refs.scrollContent2_1, 
        { y: 100, opacity: 0 }, 
        {
          y: 0, opacity: 1,
          scrollTrigger: {
            trigger: this.$refs.scrollSection2_1,
            start: "top 80%",
            end: "bottom top",
            scrub: true,
            toggleActions: "play reverse play reverse"
          }
        });

      // Анимация для секции 2.2
      gsap.fromTo(this.$refs.scrollContent2_2, 
        { y: 100, opacity: 0 }, 
        {
          y: 0, opacity: 1,
          scrollTrigger: {
            trigger: this.$refs.scrollSection2_2,
            start: "top 80%",
            end: "bottom top",
            scrub: true,
            toggleActions: "play reverse play reverse"
          }
        });

      // Анимация для секции 3
      gsap.fromTo(this.$refs.scrollContent3, 
        { y: 100, opacity: 0 }, 
        {
          y: 0, opacity: 1,
          scrollTrigger: {
            trigger: this.$refs.scrollSection3,
            start: "top 80%",
            end: "bottom top",
            scrub: true,
            toggleActions: "play reverse play reverse"
          }
        });

      // Анимация для элементов списка в секции 2.2
      gsap.fromTo(".features-list li",
        { opacity: 0, y: 20 },
        {
          opacity: 1, y: 0,
          stagger: 0.2,
          scrollTrigger: {
            trigger: ".features-list",
            start: "top 80%",
            end: "bottom top",
            scrub: true
          }
        });
    }
  }
}
</script>

<style>
@import "~bootstrap/dist/css/bootstrap.min.css";
@import "~animate.css/animate.min.css";

body, #app {
  background-color: #121212;
  color: #f8f9fa;
  font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
}

/* Стили для секций */
.scroll-animation-section {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #222;
  padding: 2rem;
}

.scroll-content {
  text-align: center;
  transition: all 0.5s ease;
}

.title {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  color: #f8f9fa;
}

.description {
  font-size: 1.25rem;
  max-width: 800px;
  margin: 0 auto;
  line-height: 1.6;
  color: #e0e0e0;
}

/* Стили для секции с игрой */
.game-details {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
  margin: 2rem 0;
}

.game-image {
  width: 100%;
  max-width: 600px;
  height: auto;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.2);
}

.game-description {
  text-align: center;
  max-width: 600px;
  margin: 0 auto;
}

.game-description h3 {
  font-size: 2rem;
  margin: 1rem 0;
  color: #f8f9fa;
}

.game-description p {
  font-size: 1.1rem;
  margin-bottom: 1rem;
  color: #e0e0e0;
}

.features-list {
  list-style: none;
  padding: 0;
  margin: 1rem 0;
}

.features-list li {
  font-size: 1.1rem;
  margin: 0.5rem 0;
  color: #e0e0e0;
  position: relative;
  overflow: hidden;
}

.features-list li::before {
  content: "✓";
  color: #00c853;
  position: absolute;
  left: -2rem;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.features-list li:hover::before {
  opacity: 1;
}

.steam-widget {
  margin-top: 20px;
  max-width: 100%;
}

/* Стили для футера */
.site-footer {
  background-color: #222;
  padding: 1rem;
  color: #f8f9fa;
}
</style>
