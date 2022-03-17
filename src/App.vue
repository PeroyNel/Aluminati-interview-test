<template>
  <div id="app">
    <!-- In the following line of code I set parameters within which the input field can operate as stated by the specification sheet. Along with that I made sure to change the v-model to v-model.number, this ensures that the results that we get are returned as typeof(Number) === true.-->
    <input type="number" v-model.number="limit" min="1" max="100" />
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
  },
  //The following computed method listens for, updates and returns the limit change from 100 when it is modified by the user.
  computed: {
    getLimit(){
      if (this.limit < 1){
        return this.limit = 1
      } else {
        return this.limit
      }
    }
  }
}
</script>

<style scoped>
</style>
