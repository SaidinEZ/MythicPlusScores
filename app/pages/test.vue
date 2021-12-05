<template>
  <div>
    <h1>{{ earth.title }}</h1>
    <p>{{ earth.description }}</p>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    const earth = await $axios.$get(`https://api.nuxtjs.dev/planets/earth`)
    return { earth }
  },
}
</script>
