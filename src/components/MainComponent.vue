<template>
  <main>
    <!--richiamo dati da SelectAreaComponent con @selected-->
    <SelectAreaComponent :options="genres" @selected="genreSelected" /> <!--Creo funzione per utilizzare i parametri-->
    <div class="container">
     <div class="card" v-for="cd in filteredArray" :key="cd.title">
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
import SelectAreaComponent from './SelectAreaComponent.vue';

export default {
name : 'MainComponent',
props : {
    cdList:Array
    },
data() {
        return {
            selected: '',
        }
    },
computed: {
    genres() {
            const array = [];
            this.cdList.forEach(element => {
                if (!array.includes(element.genre)) {
                    array.push(element.genre);
                }

            });
            console.log({ genres: array })
            return array;
        },
    filteredArray() {  // Creo Array vuoto e per ogni elemento inserisco nel FilteredArray i generi selezionati
            let array = [];
            this.cdList.forEach(item => {   // cdList Array Totale
                if (item.genre === this.selected) {
                    array.push(item)
                }
                if (this.selected === '') {
                    array = this.cdList  // Nuovo Array = FilteredArray
                }
            })
            return array
        }
    },
components : {
    SelectAreaComponent
 },
methods: {
    genreSelected(genres) {
            this.selected = genres  //la funzione raccoglie i valori di @selected e li metto in selected=''
        }
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
    .card-image:hover{
        cursor: pointer;
        opacity: 0.6;
    }
}
h4{
    color: hsl(210deg 2% 44%);
    cursor: pointer;
    opacity: 0.6;
}
</style>