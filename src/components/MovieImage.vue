<template>
  <swiper-slide>
    <div class="scale">
      <img
        id="img"
        :src="posterPath"
        class="rounded mx-auto d-block"
        @dblclick="pushMovieItem"
        style="height: 300px; width: 200px"
      />
    </div>
    <!-- <div style="content: '\00a0'; margin-top: 300px-img.offsetHeight"></div> -->
    <div
      class="d-flex justify-content-start mt-1 ps-1"
      style="color: white; opacity: 0.7"
    >
      <small>{{ movie.title }}</small>
    </div>
  </swiper-slide>
</template>

<script>
import { SwiperSlide } from "vue-awesome-swiper";

export default {
  name: "MovieImage",
  components: {
    SwiperSlide,
  },
  props: {
    movie: {
      type: Object,
    },
  },
  methods: {
    pushMovieItem: function () {
      this.$router.push({
        name: "MovieItem",
        params: { movie_id: this.movie.id },
      });
    },
  },
  computed: {
    posterPath() {
      // console.log(this.movie.poster_path.offsetHeight);
      return `https://image.tmdb.org/t/p/w200${this.movie.poster_path}`;
    },
  },
};
</script>

<style>
/* .scale {
  transform: scale(1);
  -webkit-transform: scale(1);
  -moz-transform: scale(1);
  -ms-transform: scale(1);
  -o-transform: scale(1);
  transition: all 0.3s ease-in-out;
  transition-delay: 0.2s;
}
.scale:hover {
  transform: scale(1.1);
  -webkit-transform: scale(1.1);
  -moz-transform: scale(1.1);
  -ms-transform: scale(1.1);
  -o-transform: scale(1.1);
  position: absolute;
  z-index: 1;
} */

#id {
  width: 200px;
  height: 300px;
}
.scale:hover img {
  border: 0.25vw solid rgba(255, 255, 255, 0.7);
  /* transform: scale(1.2);
  transition: all 0.3s ease-in-out;
  transition-delay: 0.2s; */
}
</style>
