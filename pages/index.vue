<template>
    <div class="container">
        <header>
            <h1 class="title">Albums de la página</h1>
        </header>
        <div class="columns is-multiline">
            <album-card v-for="album in albums" :key="album.id" :album="album"/>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import env from '../config/env';
import albumCard from '../components/albumCard.vue';
export default {
    components: { albumCard },
    name: 'indexPage',
    data(){
        return {
            albums: []
        }
    },
    created: async function() {
        let albumRes = await axios.get(`${env.endpoint}/albums`);
        this.albums = albumRes.data;
    }
}
</script>

<style scoped>

</style>