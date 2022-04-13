<template>
  <div class="text-center container mx-auto lg:w-1/4 lg:shadow-lg">
    <img
      :src="img" 
      width="400" 
      class="mx-auto
    "/>
    <h2>Title: {{ title }}</h2>
    <p>Author: {{ author }} </p>
    <p>Publisher: {{ publisher }} </p>
    <p>ISBN: {{ isbn }} </p>
    <p>Year: {{ year }} </p>
    <NuxtLink to="/books">Back to Books</NuxtLink>
  </div>
</template>
<script>
export default {
  async asyncData({ params, redirect, $axios }) {
    const { books, authors } = await $axios.$get(process.env.baseURL + '/Datastore.json');

    const filteredBook = books.find(
      (el) =>
        el.id === parseInt(params.book)
    )
    
    if (filteredBook) {
      const filteredAuthor = authors.find(
            (el) => 
              el.id === filteredBook.author
      )

      return {
        title: filteredBook.title,
        author: `${filteredAuthor.firstName} ${filteredAuthor.lastName}`,
        img: filteredBook.coverImageUrl,
        publisher: filteredBook.publisher,
        isbn: filteredBook.isbn,
        year: filteredBook.year
      }
    } else {
      redirect('/')
    }
  }
}
</script>
