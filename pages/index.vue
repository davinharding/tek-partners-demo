<template>
  <div class="text-center">
    Welcome to the books app!  Please select a tab from the top navbar to get started.
  </div>
</template>
<script>
export default {
  async asyncData() {
    const mountains = await fetch(
      'https://api.nuxtjs.dev/mountains'
    ).then((res) => res.json())

    return { mountains }
  }
}
</script>
