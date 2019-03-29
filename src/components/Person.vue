<template>
  <div class="Person">
      <img width="300px" height="300px" :src="img">
      <p>Title: {{ title }}</p>
      <p>Name: {{ name }}</p>
      <p>Gender: {{ gender }}</p>
  </div>
</template>

<script>
export default {
  name: 'Person',
  props: {
    img: String,
    name: String,
    gender: String,
    title: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
.Person
  display: flex
  justify-content: center
  align-items: center
  flex-flow: column nowrap
</style>
