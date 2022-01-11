<template>
  <div id="app">
    <header>
      <h1>Vue Router App</h1>
    </header>
    <router-view/>
  </div>
</template>

<script>

export default {
  name: 'App',
  created() {
    console.log(this.$router)
  }
};
</script>

<style>
</style>
