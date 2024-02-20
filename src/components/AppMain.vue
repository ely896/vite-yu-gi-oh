<script>
import CardYughi from './CardYughi.vue';

export default {
    name: 'AppMain',
    data() {
        return {
            
        };
    },
    mounted() {
        
    },
    components: {CardYughi}
    
}

</script>

<template>
    <main>
        <div class="container">
            <CardYughi></CardYughi>
        </div>
    </main>
   
</template>
<style  scoped>
.container {
    background-color: var(--yughi-oh-lighter);
}
</style>