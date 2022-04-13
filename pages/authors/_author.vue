<template>
  <div class="text-center container mx-auto lg:w-1/4 lg:shadow-lg">
    <img :src="img" alt="author image" class="mx-auto" />
    <p>Author: {{ author }} </p>
    <NuxtLink to="/authorsIndex">Back to Authors</NuxtLink>
  </div>
</template>
<script>
export default {
  async asyncData({ params, redirect, $axios }) {
    const { authors } = await $axios.$get(process.env.baseURL + '/Datastore.json');

    console.log(authors);

    console.log(params);

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
