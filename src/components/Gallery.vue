<template>
    <div class="gallery">
        <div class="container">
            <div class="row">
                <div class="col-md-12 images-col">
                    <img v-for="image in images" v-bind:key="image.id" :src="image.urls.regular"  :alt="image.alt_description" class="unsplash-image">
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name:'Gallery',
    data(){
        return{
            images:[],
        }
    },
    mounted(){
        axios({
        method: 'get',
        url: 'https://api.unsplash.com/photos',
        headers:{'Authorization':'Client-ID 68d3ace1d24a67372250a54167382da758efc87d4788ab96b6a06f7556ce56fd'},
        }).then(response=>{
            console.log(response.data)
            this.images = response.data
        })
        .catch(err=>{
            console.log(err)
        })
    }
}
</script>

<style scoped>
.images-col{
    column-count: 3;
    -webkit-column-count: 3;
    -moz-column-count: 3;
    -webkit-column-gap:2%;
    -moz-column-gap: 2%;
    column-gap: 2%;
    padding:2%;
}
.unsplash-image{
    display:block;
    max-width: 100%;
    height: auto;
    margin:3% auto;
}

</style>
