<template>
  <div>
    <carousel />
    <div class="tile is-ancestor">
      <div class="tile is-vertical">
        <div class="tile">
          <div class="tile is-parent is-vertical">
            <div class="notification is-light">
              <section class="hero">
                <div class="hero-body">
                  <p class="title">POST</p>
                  <p class="subtitle">article</p>
                </div>
              </section>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- components -->
    <post-home />
  </div>
</template>

<script>
import carousel from "../components/carousel.vue";
import PostHome from "../components/postHome.vue";

export default {
  components: { carousel, PostHome },
};
