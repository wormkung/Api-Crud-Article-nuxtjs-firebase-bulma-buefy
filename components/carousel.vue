<template>
  <div class="box m-2">
    <b-carousel>
      <b-carousel-item v-for="(carousel, i) in carousels" :key="i">
        <section :class="`hero is-small is-${carousel.color} `">
          <b-image class="image" :src="carousel.img"></b-image>
          <div class="hero-body has-text-centered">
            <h5 class="title is-size-6-mobile">{{ carousel.text }}</h5>
          </div>
        </section>
      </b-carousel-item>
    </b-carousel>
  </div>
</template>

<script>
export default {
  data() {
    return {
      carousels: [
        {
          text: "Slide 1",
          color: "light",
          img: "https://picsum.photos/id/43/1230/450",
        },
        {
          text: "Slide 2",
          color: "dark",
          img: "https://picsum.photos/id/40/1230/450",
        },
        {
          text: "Slide 3",
          color: "light",
          img: "https://picsum.photos/id/16/1230/450",
        },
        {
          text: "Slide 4",
          color: "dark",
          img: "https://picsum.photos/id/20/1230/450",
        },
        {
          text: "Slide 5",
          color: "light",
          img: "https://picsum.photos/id/50/1230/450",
        },
      ],
    };
  },
};
</script>
    