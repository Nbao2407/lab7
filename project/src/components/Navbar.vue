<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const isNavCollapsed = ref(true)

const toggleNavbar = () => {
  isNavCollapsed.value = !isNavCollapsed.value
}

const isActive = (path: string): boolean => {
  return router.currentRoute.value.path === path
}
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light shadow-lg bg-body">
    <div class="container">
      <button 
        class="navbar-toggler" 
        type="button" 
        @click="toggleNavbar"
        aria-controls="navbarNav" 
        aria-expanded="false" 
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      
      <div 
        class="collapse navbar-collapse" 
        :class="{ 'show': !isNavCollapsed }" 
        id="navbarNav"
      >
        <ul class="navbar-nav mx-auto">
          <li class="nav-item">
            <router-link 
              class="nav-link" 
              :class="{ 'active': isActive('/bai1') }"
              to="/bai1"
            >
              Bài 1
            </router-link>
          </li>
          <li class="nav-item">
            <router-link 
              class="nav-link" 
              :class="{ 'active': isActive('/bai2') }"
              to="/bai2"
            >
              Bài 2
            </router-link>
          </li>
          <li class="nav-item">
            <router-link 
              class="nav-link" 
              :class="{ 'active': isActive('/bai3') }"
              to="/bai3"
            >
              Bài 3
            </router-link>
          </li>
          <li class="nav-item">
            <router-link 
              class="nav-link"
              :class="{ 'active': isActive('/bai4') }"
              to="/bai4"
            >
              Bài 4
            </router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.nav-link {
  position: relative;
  margin: 0 0.25rem;
  transition: color 0.3s ease;
}

.nav-link::after {
  content: '';
  position: absolute;
  width: 0;
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: var(--bs-primary);
  transition: width 0.3s ease;
}

.nav-link:hover::after,
.nav-link.active::after {
  width: 100%;
}

.nav-item {
  padding: 5px 10px;
}

@media (max-width: 992px) {
  .nav-link {
    padding: 0.5rem 0;
  }
  
  form.d-flex {
    margin-top: 1rem;
    width: 100%;
  }
}
</style>