<template>
  <div class="hello">
    <h1>About</h1>
    <p>{{ msg }}</p>
  </div>
</template>

<script>
export default {
  name: 'about',
  data () {
    return {
      msg: 'This is about message'
    }
  }
}
</script>

<style scoped>
h1 {
  font-weight: normal;
}
</style>
