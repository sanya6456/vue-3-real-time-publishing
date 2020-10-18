<template>

  <Navigation/>
  <Grids/>
  
</template>


<script>
import Navigation from './components/navigation'
import Grids from './components/grids'

export default {
  name: 'App',
  components:{
    Navigation,
    Grids
  },

  data(){
    return{
    
    }
  },

  computed: {

  },

  methods: {

  },

}


</script>





<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.container{
  width: 100%;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>

