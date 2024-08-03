

<template>
<signup />
</template>

<script>
import signup from './signup.vue'

export default {
  name: 'App',
  components: { signup }
    
  }
 
</script>

  
  <style scoped>
  #App, #modals {
    font-family: Arial, Helvetica, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    align-items: center;
    color: #0f4d8b;
    margin-top: 60px;
  }
  
  h1 {
    border-bottom: 1px solid #ddd;
    display: inline-block;
    padding-bottom: 10px;
  }
  </style>
  