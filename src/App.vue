<script setup>
import profileImage from './assets/profile.jpeg'
import brewlyImage from './assets/brewly.png'

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

      <div class="nav-links">
        <a href="#home">Home</a>
        <a href="#about">About</a>
        <a href="#skills">Skills</a>
        <a href="#projects">Projects</a>
        <a href="#contact">Contact</a>
      </div>

      <a href="#contact" class="nav-button">
        Contact Me ↗
      </a>

    </nav>


    <!-- =========================
         HERO
    ========================== -->
    <section id="home" class="hero">

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
            I am passionate about technology, creativity, and web development.
            Welcome to my personal portfolio website!
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
            &lt;/&gt;
          </div>

          <div class="floating-card laptop-card">
            💻
          </div>

          <div class="floating-card database-card">
            🗄
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
    <section id="about" class="about-section">

      <div class="section-title about-title">

        <div class="section-icon">
          👩‍💻
        </div>

        <div>
          <p>GET TO KNOW ME</p>
          <h2>About Me</h2>
        </div>

      </div>


      <div class="about-text">

        <p>
          Hello! I'm Ni Komang Indrani Sinta Respani, an Informatics
          student with a strong interest in web development, technology,
          and digital creativity.
        </p>

        <p>
          I enjoy learning new technologies, building digital projects,
          and exploring creative ways to solve problems. Currently,
          I am developing my skills in frontend development, especially
          using HTML, CSS, JavaScript, and Vue.js.
        </p>

        <p>
          I am a fast learner, detail-oriented, and always excited to
          gain new experiences and take on new challenges.
        </p>


        <!-- HIGHLIGHTS -->
        <div class="about-highlights">

          <div class="about-item">

            <span>🎓</span>

            <div>
              <strong>Informatics Student</strong>
              <small>Information Technology</small>
            </div>

          </div>


          <div class="about-item">

            <span>💻</span>

            <div>
              <strong>Web Development</strong>
              <small>Frontend & UI Development</small>
            </div>

          </div>


          <div class="about-item">

            <span>🎨</span>

            <div>
              <strong>Digital Creativity</strong>
              <small>Design & Content Editing</small>
            </div>

          </div>

        </div>

      </div>

    </section>


  <!-- =========================
     SKILLS
========================= -->
<section id="skills" class="skills-section">

  <div class="skills-heading">

    <p>WHAT I CAN DO</p>

    <h2>My Skills</h2>

  </div>


  <div class="skills-container">

    <div
      v-for="skill in skills"
      :key="skill.name"
      class="skill-card"
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
    <section id="projects" class="projects-section">

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
          class="project-card"
        >

          <!-- PROJECT IMAGE -->
          <div class="project-image">

            <img
              v-if="project.image"
              :src="project.image"
              :alt="project.title"
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
    <section id="contact" class="contact-section">

      <div class="contact-title">

        <div class="contact-icon">
          ✉
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

  </main>
</template>