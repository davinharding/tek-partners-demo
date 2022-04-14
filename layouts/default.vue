<template>
  <div>
    <nav class="flex flex-row justify-center py-4 bg-gradient-to-r from-blue-500 to-purple-500">
      <NuxtLink to="/"><h1 class="text-3xl" >The Books App</h1></NuxtLink>
      <ul>
        <li class="hidden">
          <NuxtLink to="/">Home</NuxtLink>
        </li>
        <li>
          <NuxtLink to="/booksIndex">Books</NuxtLink>
        </li>
        <li>
          <NuxtLink to="/authorsIndex">Authors</NuxtLink>
        </li>
      </ul>      
    </nav>      
      <Nuxt />
  </div>
</template>

<style>
:root {
  --primary-color: white;
}

body {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, Roboto,
    Helvetica Neue, Arial, Noto Sans, sans-serif, Apple Color Emoji,
    Segoe UI Emoji, Segoe UI Symbol, Noto Color Emoji;
  margin: 0;
}

a {
  color: inherit;
  text-decoration: none;
}
nav a:hover {
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

main {
  margin: 0 auto;
  margin-top: 100px;
  padding: 0 1rem;
  max-width: 1280px;
  text-align: center;
}

ul {
  list-style-type: none;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
}
li {
  margin: 0 0.5rem;
  padding: 0.25rem;
  font-size: 1.2rem;
}

nav {
  padding: 0 1rem;
}
a.nuxt-link-exact-active {
  color: white;
}
</style>
