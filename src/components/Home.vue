<template>
  <div class="hello">
    <h1>Home</h1>
    <p>{{ msg }}</p>
  </div>
</template>

<script>
export default {
  name: 'home',
  data () {
    return {
      msg: 'Holar'
    }
  }
}
</script>

<style scoped>
h1 {
  font-weight: normal;
}
</style>
