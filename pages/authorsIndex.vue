<template>
  <div class="bg-gradient-to-r from-purple-500 to-blue-500 h-screen">
    <div v-for="author in authors" :key="author.id">
      <NuxtLink :to="`authors/${author.id}`">
        <ul  class="container mx-auto lg:w-3/12 lg:shadow-md mb-4 rounded-md hover:shadow-2xl bg-gray-800 text-white">
          
            <li>{{ author.firstName }} {{ author.lastName }}</li>
          
        </ul>
      </NuxtLink>
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
