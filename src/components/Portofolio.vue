<script setup lang="ts">
import { ref, reactive } from 'vue'
import { 
  Menu, 
  Github, 
  Linkedin, 
  Mail, 
  Code, 
  Server, 
  Palette, 
  Calendar, 
  ExternalLink, 
  Phone
} from 'lucide-vue-next'
import { experiences, projects, technologies, name, description, link, nickName, image1, image2 } from '@/data'

const mobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const scrollTo = (elementId) => {
  const element = document.getElementById(elementId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
  mobileMenuOpen.value = false
}
</script>

<template>
  <div class="min-h-screen bg-white">
    <!-- Navigation -->
    <nav class="fixed top-0 w-full bg-white/80 backdrop-blur-md z-50 border-b border-gray-100">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between items-center py-4">
          <div class="text-xl font-bold text-gray-900">Portfolio</div>
          <div class="hidden md:flex space-x-8">
            <a href="#home" @click="scrollTo('home')" class="text-gray-600 hover:text-gray-900 transition-colors">Home</a>
            <a href="#about" @click="scrollTo('about')" class="text-gray-600 hover:text-gray-900 transition-colors">About</a>
            <a href="#skills" @click="scrollTo('skills')" class="text-gray-600 hover:text-gray-900 transition-colors">Skills</a>
            <a href="#experience" @click="scrollTo('experience')" class="text-gray-600 hover:text-gray-900 transition-colors">Experience</a>
            <a href="#projects" @click="scrollTo('projects')" class="text-gray-600 hover:text-gray-900 transition-colors">Projects</a>
          </div>
          <button @click="toggleMobileMenu" class="md:hidden">
            <Menu class="w-6 h-6" />
          </button>
        </div>
      </div>
      
      <!-- Mobile Menu -->
      <div v-if="mobileMenuOpen" class="md:hidden bg-white border-t border-gray-100">
        <div class="px-4 py-2 space-y-2">
          <a href="#home" @click="scrollTo('home')" class="block py-2 text-gray-600">Home</a>
          <a href="#about" @click="scrollTo('about')" class="block py-2 text-gray-600">About</a>
          <a href="#skills" @click="scrollTo('skills')" class="block py-2 text-gray-600">Skills</a>
          <a href="#experience" @click="scrollTo('experience')" class="block py-2 text-gray-600">Experience</a>
          <a href="#projects" @click="scrollTo('projects')" class="block py-2 text-gray-600">Projects</a>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="pt-20 pb-16 px-4 sm:px-6 lg:px-8">
      <div class="max-w-6xl mx-auto">
        <div class="text-center py-20">
          <div class="mb-8">
            <img :src="image1" alt="Profile" class="w-32 h-32 rounded-full mx-auto mb-6 object-cover border-4 border-gray-100">
          </div>
          <h1 class="text-4xl md:text-6xl font-bold text-gray-900 mb-4">
            Hi, I'm <span class="text-blue-600">{{ nickName }}</span>
          </h1>
          <p class="text-xl md:text-2xl text-gray-600 mb-8 max-w-3xl mx-auto">
            Software engineer passionate about creating beautiful and functional digital experiences
          </p>
          <div class="flex flex-col sm:flex-row gap-4 justify-center">
            <button @click="scrollTo('projects')" class="bg-blue-600 text-white px-8 py-3 rounded-lg hover:bg-blue-700 transition-colors">
              View My Work
            </button>
            <button @click="scrollTo('about')" class="border border-gray-300 text-gray-700 px-8 py-3 rounded-lg hover:bg-gray-50 transition-colors">
              About Me
            </button>
          </div>
          <div class="flex justify-center space-x-6 mt-8">
            <a :href="link.gitHub" class="text-gray-400 hover:text-gray-600 transition-colors" target="_blank" rel="noopener noreferrer">
              <Github class="w-6 h-6" />
            </a>
            <a :href="link.linkedin" class="text-gray-400 hover:text-gray-600 transition-colors" target="_blank" rel="noopener noreferrer">
              <Linkedin class="w-6 h-6" />
            </a>
            <a :href="link.gmail" class="text-gray-400 hover:text-gray-600 transition-colors" target="_blank" rel="noopener noreferrer">
              <Mail class="w-6 h-6" />
            </a>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-16 bg-gray-50 px-4 sm:px-6 lg:px-8">
      <div class="max-w-6xl mx-auto">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">About Me</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            {{ description.heading }}
          </p>
        </div>
        <div class="grid md:grid-cols-2 gap-12 items-center">
          <div>
            <img :src="image2" alt="About" class="rounded-lg shadow-lg h-96 mx-auto">
          </div>
          <div>
            <h3 class="text-2xl font-bold text-gray-900 mb-4">My Story</h3>
            <p class="text-gray-600 mb-6">
              {{ description.content1 }}
            </p>
            <p class="text-gray-600 mb-6">
              {{ description.content2 }}
            </p>
            <div class="grid grid-cols-2 gap-4">
              <div>
                <h4 class="font-semibold text-gray-900">Location</h4>
                <p class="text-gray-600">Yogyakarta, Indonesia</p>
              </div>
              <div>
                <h4 class="font-semibold text-gray-900">Experience</h4>
                <p class="text-gray-600">2+ Years</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="py-16 px-4 sm:px-6 lg:px-8">
      <div class="max-w-6xl mx-auto">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">Skills & Technologies</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Technologies and tools I use to create amazing digital experiences
          </p>
        </div>
        
        <!-- Main Skills Categories -->
        <div class="grid lg:grid-cols-2 gap-8 mb-12">
          <!-- Frontend -->
          <div class="bg-gradient-to-br from-blue-50 to-indigo-100 p-8 rounded-2xl border border-blue-100">
            <div class="flex items-center mb-6">
              <div class="bg-blue-600 p-3 rounded-xl mr-4">
                <Code class="w-8 h-8 text-white" />
              </div>
              <h3 class="text-2xl font-bold text-gray-900">Frontend</h3>
            </div>
            <p class="text-gray-600 mb-6">Creating beautiful and interactive user interfaces</p>
            <div class="grid grid-cols-2 gap-3">
              <div class="bg-white p-3 rounded-lg shadow-sm border border-blue-200 text-center">
                <div class="text-2xl mb-2">⚡</div>
                <span class="text-sm font-medium text-gray-700">Vue.js</span>
              </div>
              <div class="bg-white p-3 rounded-lg shadow-sm border border-blue-200 text-center">
                <div class="text-2xl mb-2">⚛️</div>
                <span class="text-sm font-medium text-gray-700">React</span>
              </div>
              <div class="bg-white p-3 rounded-lg shadow-sm border border-blue-200 text-center">
                <div class="text-2xl mb-2">🚀</div>
                <span class="text-sm font-medium text-gray-700">Wordpress</span>
              </div>
              <div class="bg-white p-3 rounded-lg shadow-sm border border-blue-200 text-center">
                <div class="text-2xl mb-2">🎨</div>
                <span class="text-sm font-medium text-gray-700">Tailwind</span>
              </div>
            </div>
          </div>

          <!-- Backend -->
          <div class="bg-gradient-to-br from-green-50 to-emerald-100 p-8 rounded-2xl border border-green-100">
            <div class="flex items-center mb-6">
              <div class="bg-green-600 p-3 rounded-xl mr-4">
                <Server class="w-8 h-8 text-white" />
              </div>
              <h3 class="text-2xl font-bold text-gray-900">Backend</h3>
            </div>
            <p class="text-gray-600 mb-6">Building robust and scalable server solutions</p>
            <div class="grid grid-cols-2 gap-3">
              <div class="bg-white p-3 rounded-lg shadow-sm border border-green-200 text-center">
                <div class="text-2xl mb-2">🚂</div>
                <span class="text-sm font-medium text-gray-700">Express.js</span>
              </div>
              <div class="bg-white p-3 rounded-lg shadow-sm border border-green-200 text-center">
                <div class="text-2xl mb-2">🐍</div>
                <span class="text-sm font-medium text-gray-700">Python</span>
              </div>
              <div class="bg-white p-3 rounded-lg shadow-sm border border-green-200 text-center">
                <div class="text-2xl mb-2">🐘</div>
                <span class="text-sm font-medium text-gray-700">PostgreSQL</span>
              </div>
              <div class="bg-white p-3 rounded-lg shadow-sm border border-green-200 text-center">
                <div class="text-2xl mb-2">🍃</div>
                <span class="text-sm font-medium text-gray-700">MongoDB</span>
              </div>
            </div>
          </div>

          <!-- Design & Tools
          <div class="bg-gradient-to-br from-purple-50 to-pink-100 p-8 rounded-2xl border border-purple-100">
            <div class="flex items-center mb-6">
              <div class="bg-purple-600 p-3 rounded-xl mr-4">
                <Palette class="w-8 h-8 text-white" />
              </div>
              <h3 class="text-2xl font-bold text-gray-900">Design & Tools</h3>
            </div>
            <p class="text-gray-600 mb-6">Designing beautiful and functional experiences</p>
            <div class="grid grid-cols-2 gap-3">
              <div class="bg-white p-3 rounded-lg shadow-sm border border-purple-200 text-center">
                <div class="text-2xl mb-2">🎨</div>
                <span class="text-sm font-medium text-gray-700">Figma</span>
              </div>
              <div class="bg-white p-3 rounded-lg shadow-sm border border-purple-200 text-center">
                <div class="text-2xl mb-2">📱</div>
                <span class="text-sm font-medium text-gray-700">UI/UX</span>
              </div>
              <div class="bg-white p-3 rounded-lg shadow-sm border border-purple-200 text-center">
                <div class="text-2xl mb-2">🐙</div>
                <span class="text-sm font-medium text-gray-700">Git</span>
              </div>
              <div class="bg-white p-3 rounded-lg shadow-sm border border-purple-200 text-center">
                <div class="text-2xl mb-2">☁️</div>
                <span class="text-sm font-medium text-gray-700">AWS</span>
              </div>
            </div>
          </div> -->
        </div>

        <!-- Technology Stack -->
        <div class="text-center mb-8">
          <h3 class="text-2xl font-bold text-gray-900 mb-4">Technology Stack</h3>
          <p class="text-gray-600 mb-8">Tools and technologies I work with daily</p>
        </div>
        
        <div class="flex flex-wrap justify-center gap-4 mb-8">
          <div v-for="tech in technologies" :key="tech.name" 
               class="group bg-white hover:bg-gray-50 border border-gray-200 hover:border-gray-300 rounded-xl p-4 transition-all duration-300 hover:shadow-md hover:-translate-y-1">
            <div class="flex flex-col items-center space-y-2">
              <div class="text-3xl group-hover:scale-110 transition-transform duration-300">{{ tech.icon }}</div>
              <span class="text-sm font-medium text-gray-700">{{ tech.name }}</span>
              <span class="text-xs text-gray-500 px-2 py-1 bg-gray-100 rounded-full">{{ tech.category }}</span>
            </div>
          </div>
        </div>

        <!-- Expertise Areas -->
        <div class="bg-gray-50 rounded-2xl p-8">
          <h3 class="text-2xl font-bold text-gray-900 text-center mb-8">Areas of Expertise</h3>
          <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
            <div class="text-center">
              <div class="bg-blue-100 w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4">
                <span class="text-2xl">🚀</span>
              </div>
              <h4 class="font-semibold text-gray-900 mb-2">Performance</h4>
              <p class="text-sm text-gray-600">Optimizing applications for speed and efficiency</p>
            </div>
            <div class="text-center">
              <div class="bg-green-100 w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4">
                <span class="text-2xl">📱</span>
              </div>
              <h4 class="font-semibold text-gray-900 mb-2">Responsive Design</h4>
              <p class="text-sm text-gray-600">Creating seamless experiences across all devices</p>
            </div>
            <div class="text-center">
              <div class="bg-purple-100 w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4">
                <span class="text-2xl">🔧</span>
              </div>
              <h4 class="font-semibold text-gray-900 mb-2">Architecture</h4>
              <p class="text-sm text-gray-600">Building scalable and maintainable systems</p>
            </div>
            <div class="text-center">
              <div class="bg-yellow-100 w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4">
                <span class="text-2xl">⚡</span>
              </div>
              <h4 class="font-semibold text-gray-900 mb-2">Innovation</h4>
              <p class="text-sm text-gray-600">Implementing cutting-edge technologies</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Experience Section -->
    <section id="experience" class="py-16 bg-gray-50 px-4 sm:px-6 lg:px-8">
      <div class="max-w-6xl mx-auto">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">Experience</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            My professional journey and the companies I've had the pleasure to work with.
          </p>
        </div>
        <div class="space-y-8">
          <div v-for="(job, index) in experiences" :key="index" class="bg-white p-6 rounded-lg shadow-sm border border-gray-100">
            <div class="flex flex-col md:flex-row md:items-center md:justify-between mb-4">
              <div>
                <h3 class="text-xl font-semibold text-gray-900">{{ job.title }}</h3>
                <p class="text-blue-600 font-medium">{{ job.company }}</p>
              </div>
              <div class="text-gray-500 mt-2 md:mt-0">
                <Calendar class="w-4 h-4 inline mr-2" />
                {{ job.period }}
              </div>
            </div>
            <p class="text-gray-600 mb-4">{{ job.description }}</p>
            <div class="flex flex-wrap gap-2">
              <span v-for="tech in job.technologies" :key="tech" class="bg-gray-100 text-gray-700 px-3 py-1 rounded-full text-sm">
                {{ tech }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="py-16 px-4 sm:px-6 lg:px-8">
      <div class="max-w-6xl mx-auto">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">Featured Projects</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Here are some of the projects I've worked on that showcase my skills and passion for development.
          </p>
        </div>
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="(project, index) in projects" :key="index" class="bg-white rounded-lg shadow-sm border border-gray-100 overflow-hidden hover:shadow-md transition-shadow">
            <img :src="project.image" :alt="project.title" class="w-full h-48 object-cover">
            <div class="p-6">
              <h3 class="text-xl font-semibold text-gray-900 mb-2">{{ project.title }}</h3>
              <p class="text-gray-600 mb-4">{{ project.description }}</p>
              <div class="flex flex-wrap gap-2 mb-4">
                <span v-for="tech in project.technologies" :key="tech" class="bg-blue-100 text-blue-800 px-2 py-1 rounded text-sm">
                  {{ tech }}
                </span>
              </div>
              <div class="flex space-x-4">
                <a :href="project.link" target="_blank" rel="noopener noreferrer" class="flex items-center text-gray-600 hover:text-gray-900 transition-colors">
                  <ExternalLink class="w-4 h-4 mr-1" />
                  Live Demo
                </a>
                <!-- <a href="#" class="flex items-center text-gray-600 hover:text-gray-900 transition-colors">
                  <Github class="w-4 h-4 mr-1" />
                  Code
                </a> -->
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section class="py-16 bg-gray-900 text-white px-4 sm:px-6 lg:px-8">
      <div class="max-w-6xl mx-auto text-center">
        <h2 class="text-3xl md:text-4xl font-bold mb-4">Let's Work Together</h2>
        <p class="text-gray-300 mb-8 max-w-2xl mx-auto">
          I'm always interested in new opportunities and exciting projects. Let's connect and discuss how we can work together.
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center mb-8">
          <a href="mailto:luthfantryzm@gmail.com?subject=Mail from our Website" class="bg-blue-600 text-white px-8 py-3 rounded-lg hover:bg-blue-700 transition-colors inline-flex items-center justify-center">
            <Mail class="w-5 h-5 mr-2" />
            Send Email
          </a>
          <a href="https://wa.me/6285727702218" class="border border-gray-600 text-white px-8 py-3 rounded-lg hover:bg-gray-800 transition-colors inline-flex items-center justify-center">
            <Phone class="w-5 h-5 mr-2" />
            Schedule Call
          </a>
        </div>
        <div class="flex justify-center space-x-6">
          <a :href="link.gitHub" target="_blank" rel="noopener noreferrer" class="text-gray-400 hover:text-white transition-colors">
            <Github class="w-6 h-6" />
          </a>
          <a :href="link.linkedin" target="_blank" rel="noopener noreferrer" class="text-gray-400 hover:text-white transition-colors">
            <Linkedin class="w-6 h-6" />
          </a>
          <a href="mailto:luthfantryzm@gmail.com" target="_blank" rel="noopener noreferrer" class="text-gray-400 hover:text-white transition-colors">
            <Mail class="w-6 h-6" />
          </a>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-900 text-gray-400 py-8 px-4 sm:px-6 lg:px-8 border-t border-gray-800">
      <div class="max-w-6xl mx-auto text-center">
        <p>&copy; {{ new Date().getFullYear() }} John Doe. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<style scoped>
html {
  scroll-behavior: smooth;
}

.transition-colors {
  transition: color 0.3s ease;
}

.transition-shadow {
  transition: box-shadow 0.3s ease;
}
</style>
