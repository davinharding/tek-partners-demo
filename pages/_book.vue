<template>
  <div class="text-center">
    <h2>Title: {{ title }}</h2>
    <p>{{ author }} </p>
    <NuxtLink to="/books">Back to Mountains</NuxtLink>
  </div>
</template>
<script>
export default {
  async asyncData({ params, redirect, $axios }) {
    const { books, authors } = await $axios.$get('http://localhost:3000/Datastore.json');

    console.log(books);

    console.log(authors);

    const filteredBook = books.find(
      (el) =>
        el.id === parseInt(params.book)
    )

    
    console.log(filteredBook);
    if (filteredBook) {
      const filteredAuthor = authors.find(
            (el) => 
              el.id === filteredBook.author
      )

      return {
        title: filteredBook.title,
        author: `${filteredAuthor.firstName} ${filteredAuthor.lastName}`
      }
    } else {
      redirect('/')
    }
  }
}
</script>
