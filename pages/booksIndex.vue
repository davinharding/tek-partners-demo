<template>
  <div>
    <ul v-for="book in books" :key="book.id">
      <NuxtLink :to="`books/${book.id}`">
        <li>{{ book.title }}</li>
      </NuxtLink>
    </ul>
  </div>
</template>
<script>
export default {
  async asyncData({ $axios }) {
    const { books } = await $axios.$get('http://localhost:3000/Datastore.json');
    return { books }
  }
}
</script>
