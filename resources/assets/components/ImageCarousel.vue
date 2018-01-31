<template>
    <div class="image-carousel">
        <img :src="image"/>
        <div class="controls">
            <carousel-control dir="left" @change-image="changeImage"></carousel-control>
            <carousel-control dir="right" @change-image="changeImage"></carousel-control>
        </div>
   </div>
</template>
<script>
    import CarouselControl from '../components/CarouselControl.vue';

    export default {
        props: ['images'],
        data() {
            return {
                index: 0
            }
        },
        methods: {
            changeImage(val) {
                let newVal = this.index + parseInt(val);
                if ( newVal < 0 ){
                    this.index = this.images.length -1;
                } else if ( newVal === this.images.length ){
                    this.index = 0;
                } else {
                    this.index = newVal;
                }
            }
        },
        computed: {
            image() {
                return this.images[this.index];
            }
        },
        components: {
            CarouselControl
        }
    }
</script>
<style>
</style>
