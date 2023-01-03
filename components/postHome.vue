<template>
  <div class="columns is-multiline mt-8 box">
    <div class="column is-3" v-for="item in post" :key="item.id">
      <div class="card" @click="isCardModalActive = true">
        <div class="card-image">
          <figure class="image">
            <img :src="item.lin" height="250" width="200" />
          </figure>
        </div>
        <div class="card-content">
          <div class="media">
            <div class="media-content">
              <p class="title is-4">{{ item.name }}</p>
            </div>
          </div>
          <div class="content">
            {{ item.area }}
            <br />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      post: [],
      isCardModalActive: false,
    };
  },
  created() {
    let apiURL = "https://worm-57ba9-default-rtdb.firebaseio.com/post.json";
    axios
      .get(apiURL)
      .then((res) => {
        this.post = res.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style scoped >
</style>