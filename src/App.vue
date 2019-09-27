<template>
  <div id="app">
    <component :is="selectedComponent"></component>

  </div>
</template>


<script>

import first from './components/First'
import second from './components/Second'

export default {
  data(){
    return {
      selectedComponent : 'app-first',
      isStarted : false
    }
  },
  components : { 
    'app-first' : first ,
    'app-second': second
  },
  mounted () {
  
    this.$animejs({
      targets : '.first-one',
      opacity : [
        {value : 1 , duration : 500 },
        {value : .2, duration : 1000 },
      ],
      scale : [
        {value : 0.5 , duration : 0 },
        {value : 2, duration : 1500 ,  },
      ],
      easing : 'linear'
    });



      setTimeout(()=>{

        this.selectedComponent = 'app-second';
        console.log('finished')
    
    },1500)

 


  },
  updated(){
    console.log('updated')
        this.$animejs({
          targets : '.second-one',
          opacity : [
            {value : 0.5, duration : 0 },
            {value :  1, duration : 300 },
      ],
      easing : 'linear'
      });
  }
  
}
</script>

<style lang="scss">

#app {
  height: 100vh;
}

.first-one {
  background-color: yellow;
  scale: 0;
  
  }
.second-one {
  background-color: green;
}

</style>
