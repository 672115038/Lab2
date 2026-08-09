<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <!-- <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView /> -->
  <div class="text-center font-sans text-grey-700 antialiased">
    <header>
      <div class="wrapper">
        <nav>
          <RouterLink :to="{ name: 'event-list-view' }">Event</RouterLink>
          <RouterLink :to="{ name: 'student-list-view' }">Students</RouterLink>
          <RouterLink :to="{ name: 'about' }">About</RouterLink>
        </nav>
        <div class="page-size-links">
          <span>Page size:</span>
          <RouterLink :to="{ name: 'event-list-view', query: { size: 1 } }">1</RouterLink>
          <RouterLink :to="{ name: 'event-list-view', query: { size: 2 } }">2</RouterLink>
          <RouterLink :to="{ name: 'event-list-view', query: { size: 4 } }">4</RouterLink>
        </div>
      </div>
    </header>
    <!-- <h1>Events For Good</h1> -->
    <RouterView />
  </div>
</template>

<style>
nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

h2 {
  font-size: 20px;
}

@keyframes yellowFade {
  from {
    background-color: yellow;
  }
  to {
    background-color: transparent;
  }
}

#flashMessage {
  animation: yellowFade 3s ease-in-out;
}
</style>
