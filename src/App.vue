<template>
  <div id="app">
    <HeaderComponent />
    <div class="load" v-if="loading">.....LOADING......</div>
    <MainComponent :cdList='cdCard'/>
  </div>
</template>

<script>
import axios from 'axios';
import HeaderComponent from '@/components/HeaderComponent.vue'
import MainComponent from '@/components/MainComponent.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent
  },
  data(){
    return {
      cdCard : [],
      loading : true,
    }
  },
  created(){
    axios 
      .get('https://flynn.boolean.careers/exercises/api/array/music')
      .then((response)=>{
        this.cdCard = response.data.response
        this.loading = false
      })
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.load{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50% , -50%);
}
img{
  width: 100%;
}
</style>
