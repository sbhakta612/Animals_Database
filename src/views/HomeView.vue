<template>
  <ul>
    <li v-for="animal in animalsList">
      <RouterLink :to="`/about?name=${animal.name}`">{{ animal.name }}</RouterLink>
    </li>
  </ul>
</template>
<script>
export default {
  data() {
    return {
      animalsList: []
    }
  },
  async created() {
    const response = await fetch('http://localhost:3000/animals/')
    const result = await response.json()
    this.animalsList = result.results
  }
}
</script>
