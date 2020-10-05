<template>
  <div class="mb-5">
    <div class="owl-carousel owl-theme home-slider owl-loaded owl-drag">
      <vue-flux
        :options="vfOptions"
        :images="vfImages"
        :transitions="vfTransitions"
        :captions="vfCaptions"
        ref="slider"
      >
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
      <!-- <flux-button v-if="mounted" :slider="$refs.slider" class="bg-danger"/> -->
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
  FluxPreloader,
} from "vue-flux";
export default {
  name: "Carousel",
  data: () => ({
    vfOptions: {
      autoplay: true,
    },
    vfImages: [],
    vfTransitions: ["round1", "warp", "slide"],
    vfCaptions: [],
    mounted: null,
  }),
  mounted: function () {
    this.mounted = true;
    this.getFeaturedPosts();
  },
  methods: {
    getFeaturedPosts() {
      this.axios
        .get("http://127.0.0.1:8000/api/featuredPosts")
        .then((response) => {
          let posts = response.data;
          for (let i = 0; i < posts.length; i++) {
            this.vfImages.push(
              "http://127.0.0.1:8000/" + response.data[i].image
            );
            this.vfCaptions.push(
              response.data[i].title + " - " + response.data[i].category.name
            );
          }
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
  components: {
    VueFlux,
    FluxCaption,
    FluxControls,
    FluxIndex,
    FluxPagination,
    FluxPreloader,
  },
};
</script>

<style>
</style>