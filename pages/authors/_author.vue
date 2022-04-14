<template>
  <div class="bg-gradient-to-r from-purple-500 to-blue-500 h-screen">
    <div class="text-center container mx-auto lg:w-1/4 lg:shadow-lg rounded-md bg-gray-800 text-white decoration-inherit">
      <img :src="img" alt="author image" class="mx-auto pt-2 rounded-md" />
      <p>Author: {{ author }} </p>
      <NuxtLink to="/authorsIndex" class="font-bold">Back to Authors</NuxtLink>
    </div>
  </div>
</template>
<script>
export default {
  async asyncData({ params, redirect, $axios }) {
    const { authors } = await $axios.$get(process.env.baseURL + '/Datastore.json');

    const filteredAuthor = authors.find(
          (el) => 
            el.id === parseInt(params.author)
    )
    if (filteredAuthor) {
      return {
        author: `${filteredAuthor.firstName} ${filteredAuthor.lastName}`,
        img: filteredAuthor.imageUrl
      }
    } else {
      redirect('/')
    }
  }
}
</script>
