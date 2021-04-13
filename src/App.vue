<template>
  <div id="app">
    <Nav />
    <Input />
  </div>
</template>

<script>
import Nav from './components/Nav.vue'
import Input from './components/Input.vue'

export default {
  name: 'App',
  components: {
    Nav,
    Input
  }
}
</script>

<style>
#app {

}
</style>
