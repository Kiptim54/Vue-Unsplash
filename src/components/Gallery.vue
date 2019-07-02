<template>
    <div class="gallery">
        <div class="container-fluid">
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
process.env.VUE_APP_CLIENT_ID

export default {
    name:'Gallery',
    data(){
        return{
            images:[],
        }
    },
    mounted(){
        console.log('client id', process.env.VUE_APP_CLIENT_ID)
        axios({
        method: 'get',
        url: 'https://api.unsplash.com/photos',
        headers:{'Authorization':`Client-ID ${process.env.VUE_APP_CLIENT_ID}`},
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
    -webkit-column-gap:auto;
    -moz-column-gap: auto;
    column-gap: auto;
    padding:2%;
}
.unsplash-image{
    display:block;
    max-width: 100%;
    height: auto;
    margin:3% auto;
}

</style>
