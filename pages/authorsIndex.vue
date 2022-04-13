<template>
  <div class="container mx-auto lg:w-1/4 lg:shadow-lg">
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
    const { authors } = await $axios.$get(process.env.baseURL + '/Datastore.json');
    return { authors }
    }
}
</script>
