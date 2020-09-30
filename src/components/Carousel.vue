<template>
    <div class="mb-5">
        <div class="owl-carousel owl-theme home-slider owl-loaded owl-drag">
            <vue-flux :options="vfOptions" :images="vfImages" :transitions="vfTransitions" :captions="vfCaptions"
                ref="slider">

                <template v-slot:preloader>
                    <flux-preloader />
                </template>

                <template v-slot:caption>
                    <flux-caption />
                </template>

                <template v-slot:controls>
                    <flux-controls />
                </template>

                <template v-slot:pagination>
                    <flux-pagination />
                </template>

                <template v-slot:index>
                    <flux-index />
                </template>
            </vue-flux>
            <!-- <flux-caption v-if="mounted" :slider="$refs.slider" class="bg-danger"/> -->
        </div>

    </div>
</template>

<script>
    import {
        VueFlux,
        FluxCaption,
        FluxControls,
        FluxIndex,
        FluxPagination,
        FluxPreloader
    } from 'vue-flux';
    export default {
        name: 'Carousel',
        data: () => ({
            vfOptions: {
                autoplay: true
            },
            vfImages: ['images/img_2.jpg', 'images/img_3.jpg', 'images/img_1.jpg'],
            vfTransitions: ['round1', 'warp', 'slide'],
            vfCaptions: [
                'Caption for image 1',
                'Caption for image 2',
                'Caption for image 3',
            ],
            mounted: null
        }),
        mounted: function () {
            this.mounted = true;
        },
        methods: {

        },
        components: {
            VueFlux,
            FluxCaption,
            FluxControls,
            FluxIndex,
            FluxPagination,
            FluxPreloader,
        },
    }
</script>

<style>

</style>