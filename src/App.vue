<template>
  <div id="app">
    //In the following line of code I set parameters within which the input field can operate as stated by the specification sheet.
    <input type="number" v-model="limit" min="1" max="100" />
    <Numbers/>
  </div>
</template>

<script>
import Numbers from '@/components/Numbers';

export default {
  name: 'App',
  components: {Numbers},
  data()
  {
    return {
      limit: 100
    }
  }
}
</script>

<style scoped>
</style>
