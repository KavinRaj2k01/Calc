<template>
<div>
<calculator :titles='title' />
</div>
</template>

<script>
import calculator from './components/Calculator'
export default {
  name: 'App',
  components:{
    calculator,
  },
  data()
  {
    return{
      title:'CALCULATOR',
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
