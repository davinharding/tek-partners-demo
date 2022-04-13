<template>
  <div>
    <div v-for="author in authors" :key="author.id">
      <ul  class="container mx-auto lg:w-2/12 lg:shadow-lg my-4 rounded-md hover:shadow-2xl">
        <NuxtLink :to="`authors/${author.id}`">
          <li>{{ author.firstName }} {{ author.lastName }}</li>
        </NuxtLink>
      </ul>
    </div>
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
