<script>
import axios from 'axios';

export default {
    name: 'CardYughi',
    data() {
        return {
            base_api_url: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0',
            cards: [],
        };
    },
    mounted() {
        //console.log(this.base_api_url); serve per verificare se l'indirizzo dove prenderò i dati mi rispondere è giusto
        axios
            .get(this.base_api_url)
            //con then catturo i dati che ho chiesto inserendo l'indirizzo api_url
            .then((response) => {
                console.log(response);
                this.cards = response.data.data;
                console.log(response.data); //tutti i data incluse le della paginazione
                console.log(response.data.results); //only characters results
            })
            //catch serve per ricevere informazioni su eventuali errori
            .catch((error) => {
                console.error(error);
            });
    },

}

</script>

<template>
    <div class="container">
        <div class="row">
            
            <div v-for="card in cards" :key="card.id" class="col-12 col-sm-6 col-md-4">
                <div class="card">
                    
                    <img :src="card.card_images[0]?.image_url" alt="">
                    <div class="card-body">
                        <h3 class="card-title">{{ card.name }}</h3>
                        <h4 class="card-text">{{ card.type }}</h4>
                        
                        <h5 class="card-text" v-if="card.archetype"> {{ card.archetype }}</h5>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
  
<style  scoped>
.card {
    max-width: 100%;
    object-fit: cover;
    background-color: var(--yughi-oh-primary);
    text-align: center;
    
}


</style>