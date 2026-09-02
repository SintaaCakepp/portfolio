
App · VUE
<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
 
import profileImage from './assets/profile.jpeg'
import brewlyImage from './assets/brewly.png'
import portfolioImage from './assets/portfolio.jpeg'
 
const menuOpen = ref(false)
const activeSection = ref('home')
const showBackToTop = ref(false)
const currentYear = new Date().getFullYear()
 
const sectionIds = ['home', 'about', 'skills', 'projects', 'contact']
 
let sectionObserver = null
let revealObserver = null
 
const skills = [
  { name: 'HTML', icon: 'fa-brands fa-html5' },
  { name: 'CSS', icon: 'fa-brands fa-css3-alt' },
  { name: 'JavaScript', icon: 'fa-brands fa-js' },
  { name: 'Vue.js', icon: 'fa-brands fa-vuejs' },
  { name: 'Canva', icon: '✦' },
  { name: 'CapCut', icon: '✂' }
]
 
const projects = [
  {
    number: '01',
    title: 'Personal Portfolio',
    description:
      'A modern personal portfolio website designed to showcase my profile, skills, and projects.',
    tech: ['Vue.js', 'HTML', 'CSS'],
    type: 'Web Development',
    image: portfolioImage,
    link: 'https://cyntaa.vercel.app/'
  },
  {
    number: '02',
    title: 'Brewly Coffee App',
    description:
      'A coffee shop mobile application featuring user authentication, product browsing, shopping cart, checkout, and order history.',
    tech: ['Java', 'Firebase', 'Firestore'],
    type: 'Mobile Application',
    image: brewlyImage,
    link: 'https://github.com/SintaaCakepp/Brewly-Coffee-App'
  }
]
 
function setupScrollSpy() {
  sectionObserver = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          activeSection.value = entry.target.id
        }
      })
    },
    { rootMargin: '-40% 0px -55% 0px', threshold: 0 }
  )
 
  sectionIds.forEach((id) => {
    const el = document.getElementById(id)
    if (el) sectionObserver.observe(el)
  })
}
 
function setupScrollReveal() {
  revealObserver = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible')
          revealObserver.unobserve(entry.target)
        }
      })
    },
    { threshold: 0.15 }
  )
 
  document.querySelectorAll('.reveal').forEach((el) => {
    revealObserver.observe(el)
  })
}
 
function handleScroll() {
  showBackToTop.value = window.scrollY > 400
}
 
function scrollToTop() {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}
 
function handleClickOutside(event) {
  if (!menuOpen.value) return
  const nav = document.querySelector('.navbar')
  if (nav && !nav.contains(event.target)) {
    menuOpen.value = false
  }
}
 
onMounted(() => {
  setupScrollSpy()
  setupScrollReveal()
  window.addEventListener('scroll', handleScroll)
  document.addEventListener('click', handleClickOutside)
})
 
onUnmounted(() => {
  if (sectionObserver) sectionObserver.disconnect()
  if (revealObserver) revealObserver.disconnect()
  window.removeEventListener('scroll', handleScroll)
  document.removeEventListener('click', handleClickOutside)
})
</script>
 
<template>
  <main>
 
    <!-- =========================
         NAVBAR
    ========================== -->
    <nav class="navbar">
 
      <a href="#home" class="logo">
        Cyntaa<span>.</span>
      </a>
 
 
      <!-- DESKTOP MENU -->
      <div class="nav-links">
 
        <a
          href="#home"
          :class="{ active: activeSection === 'home' }"
        >
          Home
        </a>
 
        <a
          href="#about"
          :class="{ active: activeSection === 'about' }"
        >
          About
        </a>
 
        <a
          href="#skills"
          :class="{ active: activeSection === 'skills' }"
        >
          Skills
        </a>
 
        <a
          href="#projects"
          :class="{ active: activeSection === 'projects' }"
        >
          Projects
        </a>
 
        <a
          href="#contact"
          :class="{ active: activeSection === 'contact' }"
        >
          Contact
        </a>
 
      </div>
 
 
      <!-- DESKTOP CONTACT -->
      <a
        href="#contact"
        class="nav-button"
      >
        Contact Me ↗
      </a>
 
 
      <!-- MOBILE MENU BUTTON -->
      <button
        class="menu-toggle"
        @click="menuOpen = !menuOpen"
        aria-label="Toggle navigation"
      >
        <i
          :class="
            menuOpen
              ? 'fa-solid fa-xmark'
              : 'fa-solid fa-bars'
          "
        ></i>
      </button>
 
 
      <!-- MOBILE MENU -->
      <div
        v-if="menuOpen"
        class="mobile-menu"
      >
 
        <a
          href="#home"
          @click="menuOpen = false"
        >
          Home
        </a>
 
        <a
          href="#about"
          @click="menuOpen = false"
        >
          About
        </a>
 
        <a
          href="#skills"
          @click="menuOpen = false"
        >
          Skills
        </a>
 
        <a
          href="#projects"
          @click="menuOpen = false"
        >
          Projects
        </a>
 
        <a
          href="#contact"
          @click="menuOpen = false"
        >
          Contact
        </a>
 
      </div>
 
    </nav>
 
 
    <!-- =========================
         HERO
    ========================== -->
    <section
      id="home"
      class="hero"
    >
 
      <div class="hero-content">
 
        <!-- TEXT -->
        <div class="hero-text">
 
          <p class="intro">
            Hello, I'm 👋
          </p>
 
          <h1>
            Ni Komang Indrani
            <br />
            <span>Sinta Respani</span>
          </h1>
 
          <h2>
            Informatics Student & Aspiring Web Developer
          </h2>
 
          <p class="hero-description">
            I'm passionate about technology, web development, and digital creativity. Welcome to my personal portfolio!
          </p>
 
 
          <!-- BUTTON -->
          <div class="hero-buttons">
 
            <a
              href="#projects"
              class="primary-btn"
            >
              View My Work
              <span>→</span>
            </a>
 
            <a
              href="#about"
              class="secondary-btn"
            >
              About Me
            </a>
 
            <a
              href="/cv.pdf"
              target="_blank"
              rel="noopener noreferrer"
              download
              class="secondary-btn"
            >
              <i class="fa-solid fa-download"></i>
              Download CV
            </a>
 
          </div>
 
 
          <!-- SOCIAL MEDIA -->
          <div class="social-links">
 
            <!-- GitHub -->
            <a
              href="https://github.com/SintaaCakepp"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="GitHub"
            >
              <i class="fa-brands fa-github"></i>
            </a>
 
            <!-- Instagram -->
            <a
              href="https://www.instagram.com/sintaacakepp_/"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="Instagram"
            >
              <i class="fa-brands fa-instagram"></i>
            </a>
 
            <!-- TikTok -->
            <a
              href="https://www.tiktok.com/@sintaacakepp"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="TikTok"
            >
              <i class="fa-brands fa-tiktok"></i>
            </a>
 
            <!-- WhatsApp -->
            <a
              href="https://wa.me/62881037363537"
              target="_blank"
              rel="noopener noreferrer"
              aria-label="WhatsApp"
            >
              <i class="fa-brands fa-whatsapp"></i>
            </a>
 
            <!-- Email -->
            <a
              href="mailto:indyopeh@gmail.com"
              aria-label="Email"
            >
              <i class="fa-solid fa-envelope"></i>
            </a>
 
          </div>
 
        </div>
 
 
        <!-- PROFILE -->
        <div class="profile-area">
 
          <div class="profile-circle">
 
            <img
              :src="profileImage"
              alt="Ni Komang Indrani Sinta Respani"
              class="profile-image"
            />
 
          </div>
 
 
          <!-- FLOATING ICONS -->
         <div class="floating-card code-card">
  <i class="fa-solid fa-code"></i>
</div>
 
<div class="floating-card laptop-card">
  <i class="fa-solid fa-laptop-code"></i>
</div>
 
<div class="floating-card database-card">
  <i class="fa-solid fa-database"></i>
</div>
 
 
          <!-- DECORATION -->
          <div class="dots dots-one"></div>
          <div class="dots dots-two"></div>
 
        </div>
 
      </div>
 
    </section>
 
 
    <!-- =========================
         ABOUT
    ========================== -->
    <section
      id="about"
      class="about-section"
    >
 
      <div class="section-title about-title">
 
        <div class="section-icon">
  <i class="fa-solid fa-user"></i>
</div>
 
        <div>
          <p>GET TO KNOW ME</p>
          <h2>About Me</h2>
        </div>
 
      </div>
 
 
      <div class="about-text">
 
        <p>
          Hello! I'm Ni Komang Indrani Sinta Respani, an Informatics student
          passionate about web development, technology, and digital creativity.
        </p>
 
        <p>
          I enjoy learning new technologies, building digital projects, and
          exploring creative ways to solve problems. I'm currently developing
          my frontend skills, especially with HTML, CSS, JavaScript, and Vue.js.
        </p>
 
        <p>
          I'm a fast learner, detail-oriented, and always excited to gain
          new experience and take on new challenges.
        </p>
 
 
        <!-- HIGHLIGHTS -->
        <div class="about-highlights">
 
          <div class="about-item reveal">
 
            <div class="about-icon">
              <i class="fa-solid fa-graduation-cap"></i>
            </div>
 
            <div class="about-item-text">
              <strong>Informatics Student</strong>
              <small>Information Technology</small>
            </div>
 
          </div>
 
 
          <div class="about-item reveal">
 
            <div class="about-icon">
              <i class="fa-solid fa-code"></i>
            </div>
 
            <div class="about-item-text">
              <strong>Web Development</strong>
              <small>Frontend &amp; UI Development</small>
            </div>
 
          </div>
 
 
          <div class="about-item reveal">
 
            <div class="about-icon">
              <i class="fa-solid fa-pen-nib"></i>
            </div>
 
            <div class="about-item-text">
              <strong>Digital Creativity</strong>
              <small>Design &amp; Content Editing</small>
            </div>
 
          </div>
 
        </div>
 
      </div>
 
    </section>
 
 
    <!-- =========================
         SKILLS
    ========================== -->
    <section
      id="skills"
      class="skills-section"
    >
 
      <div class="skills-heading">
 
        <p>WHAT I CAN DO</p>
 
        <h2>My Skills</h2>
 
      </div>
 
 
      <div class="skills-container">
 
        <div
          v-for="skill in skills"
          :key="skill.name"
          class="skill-card reveal"
        >
 
          <div class="skill-icon">
 
            <i
              v-if="skill.icon.startsWith('fa-')"
              :class="skill.icon"
            ></i>
 
            <span v-else>
              {{ skill.icon }}
            </span>
 
          </div>
 
          <h3>
            {{ skill.name }}
          </h3>
 
        </div>
 
      </div>
 
    </section>
 
 
    <!-- =========================
         PROJECTS
    ========================== -->
    <section
      id="projects"
      class="projects-section"
    >
 
      <div class="projects-heading">
 
        <p>MY WORK</p>
 
        <h2>
          Featured
          <br />
          Projects
        </h2>
 
      </div>
 
 
      <div class="project-list">
 
        <article
          v-for="project in projects"
          :key="project.title"
          class="project-card reveal"
        >
 
          <!-- PROJECT IMAGE -->
          <div class="project-image">
 
            <img
              v-if="project.image"
              :src="project.image"
              :alt="project.title"
              loading="lazy"
            />
 
            <span v-else>
              {{ project.number }}
            </span>
 
            <div class="project-image-text">
              {{ project.type }}
            </div>
 
          </div>
 
 
          <!-- PROJECT CONTENT -->
          <div class="project-content">
 
            <p class="project-number">
              PROJECT {{ project.number }}
            </p>
 
            <h3>
              {{ project.title }}
            </h3>
 
            <p class="project-description">
              {{ project.description }}
            </p>
 
 
            <!-- TECHNOLOGY -->
            <div class="tech-list">
 
              <span
                v-for="tech in project.tech"
                :key="tech"
              >
                {{ tech }}
              </span>
 
            </div>
 
 
            <!-- LINK -->
            <a
              v-if="project.link"
              :href="project.link"
              target="_blank"
              rel="noopener noreferrer"
              class="project-link"
            >
              View Project
              <span>→</span>
            </a>
 
            <span
              v-else
              class="project-link disabled"
            >
              Coming Soon
              <span>↗</span>
            </span>
 
          </div>
 
        </article>
 
      </div>
 
    </section>
 
 
    <!-- =========================
         CONTACT
    ========================== -->
    <section
      id="contact"
      class="contact-section"
    >
 
      <div class="contact-title">
 
       <div class="contact-icon">
  <i class="fa-solid fa-envelope"></i>
</div>
 
        <div>
          <p>LET'S CONNECT</p>
          <h2>Get In Touch</h2>
        </div>
 
      </div>
 
 
      <div>
 
        <p class="contact-description">
          Feel free to contact me for collaboration
          <br />
          or any exciting opportunities!
        </p>
 
        <a
          href="mailto:indyopeh@gmail.com"
          class="contact-email"
        >
          indyopeh@gmail.com
        </a>
 
      </div>
 
 
      <a
        href="mailto:indyopeh@gmail.com"
        class="contact-button"
      >
        Contact Me ↗
      </a>
 
    </section>
 
 
    <!-- =========================
         FOOTER
    ========================== -->
    <footer class="site-footer">
      <p>
        © {{ currentYear }} Ni Komang Indrani Sinta Respani. All rights reserved.
      </p>
    </footer>
 
 
    <!-- =========================
         BACK TO TOP
    ========================== -->
    <button
      class="back-to-top"
      :class="{ visible: showBackToTop }"
      @click="scrollToTop"
      aria-label="Back to top"
    >
      <i class="fa-solid fa-arrow-up"></i>
    </button>
 
  </main>
</template>
 
