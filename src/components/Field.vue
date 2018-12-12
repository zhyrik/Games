<template>
  <div class="field">
    <count-colors></count-colors>
  </div>
</template>

<script>
import countColors from './countColors/Main'
export default {
  name: 'HelloWorld',
  components: {
    countColors
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.field{
  margin: 0 auto;
  width: 550px;
  height: 400px;
  border: 1px solid black;
}
</style>
