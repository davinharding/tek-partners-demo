<template>
  <div > 
    <div v-for="book in books" :key="book.id">  
      <NuxtLink :to="`books/${book.id}`">
        <ul  class="container mx-auto lg:w-4/12 lg:shadow-lg my-4 rounded-md hover:shadow-2xl">
          <div>
            <img :src="book.coverImageUrl" width="75" />
          </div>
          <div>
            <li class="text-left">{{ book.title }}</li>
            <li class="text-sm">{{ book.authorName }} </li>
            <li class="text-sm">{{ book.year }} </li>
          </div>
        </ul>    
      </NuxtLink>
    </div>
  </div>
</template>
<script>
export default {

  

  async asyncData({ $axios }) {
    const { books, authors } = await $axios.$get(process.env.baseURL + '/Datastore.json');

    books.map((e) =>{
      const respAuthor = authors.find((el) => el.id === e.author);
      e.authorName = respAuthor.firstName + ' ' + respAuthor.lastName;
    })
    console.log(books, authors);
    return { books }
  }
}
</script>
