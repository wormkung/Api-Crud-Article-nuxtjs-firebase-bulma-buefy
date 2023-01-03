<template>
  <div>
    <div class="tile is-parent">
      <article class="tile is-child notification is-dark">
        <p class="title">Post List.</p>
        <p class="subtitle">Admin</p>
        <div class="level-right">
          <nuxt-link to="postlist/insert"
            ><b-button size="is-large" icon-left="plus"
              >Add
            </b-button></nuxt-link
          >
        </div>
      </article>
    </div>
    <div class="columns is-multiline mt-8 box">
      <div class="column is-3" v-for="item in data" :key="item.id">
        <div class="card">
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
          <div class="level-right">
            <nuxt-link :to="{ path: `/postlist/${item.id}` }">
              <b-button
                label="Update"
                type="is-warning"
                icon-left="pen"
                size="is-small"
              />
            </nuxt-link>
            <b-button
              @click.prevent="deleteStudent(item.id)"
              label="Delete"
              type="is-danger"
              icon-left="close"
              size="is-small"
            />
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
    return {};
  },
  asyncData(context) {
    return axios
      .get("https://worm-57ba9-default-rtdb.firebaseio.com/post.json")
      .then((res) => {
        const data = [];
        for (const key in res.data) {
          data.push({ ...res.data[key], id: key });
        }
        return { data };
      });
  },
  methods: {
    deleteStudent(id) {
      let apiURL = `https://worm-57ba9-default-rtdb.firebaseio.com/post/${id}.json`;
      let indexOfArrayItem = this.data.findIndex((i) => i.id === id);
      if (window.confirm("Do you really want to delete?")) {
        axios
          .delete(apiURL)
          .then(() => {
            this.data.splice(indexOfArrayItem, 1);
            this.$buefy.notification.open({
              duration: 5000,
              message: `Data has been deleted. <b>bottom</b>`,
              position: "is-bottom-right",
              type: "is-danger",
            });
          })
          .catch((error) => {
            console.log(error);
          });
      }
    },
  },
};
</script>

<style scoped >
</style>
