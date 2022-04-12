<template>
  <div>
    <ul v-for="author in authors" :key="author.id">
      <NuxtLink :to="`authors/${author.id}`">
        <li>{{ author.firstName }} {{ author.lastName }}</li>
      </NuxtLink>
    </ul>
  </div>
</template>
<script>
export default {
    async asyncData({ $axios }) {
    const { authors } = await $axios.$get('http://localhost:3000/Datastore.json');
    return { authors }
    }
}
</script>
