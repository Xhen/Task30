<template>
  <div id="app">
    <logo></logo>
    <div id="nav">
      <router-link to="/">Dashboard</router-link>
    </div>
    <router-view/>
    <!-- Inject -->
  </div>
</template>

<script>
  import Logo from './components/Logo.vue'
export default {
  name: 'App',
  components: {
    Logo
  }
}
</script>


<style lang="sass">

@import url('https://fonts.googleapis.com/css?family=Raleway|Roboto')

*
  box-sizing: border-box

#app
  text-align: center
  color: #2c3e50
  font-family: 'Roboto', sans-serif

#nav
  font-size: 1.2rem
  padding: 30px
  a
    font-weight: bold
    color: #2c3e50

    &.router-link-exact-active
      color: #42b983
</style>
