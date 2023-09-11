<template>
  <header>
    <h1>{{ title }}</h1>
  </header>  
</template>

<script>
export default {
  props:['title']
}
</script>

<style scoped>
header {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 5rem;
  margin: 0;
  background-color: #640032
}

h1 {
  color: white;
  margin: 0;
}
</style>