<template>
    <div class="w-full flex p-8">
        <input-gallery @passData="dataImg = $event"></input-gallery>
        <view-gallery :theData="dataImg"></view-gallery>
    </div>
</template>

<script>
    import InputGallery from './components/InputGallery.vue';
    import ViewGallery from './components/ViewGallery.vue';

    export default {
        data(){
            return{
                dataImg: [],
            }
        },
        components: {
            InputGallery,
            ViewGallery,
        }
    }
</script>

<style>

</style>
