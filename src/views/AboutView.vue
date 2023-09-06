<template>
  <div>
    {{ name }}
  </div>
  <div>{{ color }}</div>
  <div>{{ type }}</div>
</template>
<script>
export default {
  data() {
    return {
      name: 'N/a',
      color: 'N/a',
      type: 'N/a'
    }
  },
  async created() {
    console.log(this.$route)
    const nameParam = this.$route.query.name
    const response = await fetch('http://localhost:3000/animals/' + nameParam)
    const result = await response.json()

    this.name = result.name
    this.color = result.color
    this.type = result.type
  }
}
</script>
