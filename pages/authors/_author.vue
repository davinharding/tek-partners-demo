<template>
  <div class="text-center">
    <p>Author: {{ author }} </p>
    <NuxtLink to="/authorsIndex">Back to Authors</NuxtLink>
  </div>
</template>
<script>
export default {
  async asyncData({ params, redirect, $axios }) {
    const { authors } = await $axios.$get('http://localhost:3000/Datastore.json');

    console.log(authors);

    console.log(params);

    const filteredAuthor = authors.find(
          (el) => 
            el.id === parseInt(params.author)
    )
    if (filteredAuthor) {
      return {
        author: `${filteredAuthor.firstName} ${filteredAuthor.lastName}`,
      }
    } else {
      redirect('/')
    }
  }
}
</script>
