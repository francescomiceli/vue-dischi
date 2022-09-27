<template>
  <main>
    <div class="container">
     <div class="card" v-for="cd in cdList" :key="cd.title">
        <div class="card-image">
            <img :src="cd.poster" alt="">
        </div>
         <h3>{{cd.title}}</h3>
         <h4>{{cd.author}} <h4>{{cd.year}}</h4> </h4>
         
     </div>
</div>
  </main>
</template>

<script>
export default {
name : 'MainComponent',
props : {
    cdList:Array
}
}
</script>

<style lang="scss" scoped>
main{
    background-color: hsl(209deg 33% 17%);
}
.container{
    width: 1200px;
    margin: 0 auto;
    padding: 30px 0;
    display: flex;
    flex-wrap: wrap;
}    
.card{
    width: calc( 100% / 5 - 40px);
    height: 400px;
    margin: 20px;
    text-align: center;
    background-color: hsl(210deg 22% 23%);
    color: white;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
    .card-image{
        width: 150px;
        height: 150px;
    }
}
h4{
    color: hsl(210deg 2% 44%);
}
</style>