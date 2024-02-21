<script>
import axios from 'axios';

export default {
    name: 'CardYughi',
    data() {
        return {
            base_api_url: 'https://db.ygoprodeck.com/api/v7/cardinfo.php',
            cards: [],
        };
    },
    mounted() {
        
        axios
            .get(this.base_api_url)
            
            .then((response) => {
                console.log(response);
                this.cards = response.data.data;
                console.log(response.data); 
                console.log(response.data.results); 
            })
            
            .catch((error) => {
                console.error(error);
            });
    },

}

</script>

<template>
    <div class="container">
        <div class="row">
            
            <div v-for="card in cards" :key="card.id" class="col-12 col-sm-6 col-md-4 col-lg-4 col-xl-3 col-xxl-3">
                <div class="card">
                    
                    <img :src="card.card_images[0]?.image_url_cropped" alt="">
                    <div class="card-body">
                        <h3 >{{ card.name }}</h3>
                        
                        
                        <h4 v-if="card.archetype"> {{ card.archetype }}</h4>
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

.card-body {
    height: 100px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    & h3 {
        color: var(--yughi-oh-lighter);
    }

}


</style>