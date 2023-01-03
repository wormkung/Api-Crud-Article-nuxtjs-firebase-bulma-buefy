<template>
  <div>
    <section class="hero is-dark has-text-centered">
      <div class="hero-body">
        <p class="title">Update Data</p>
      </div>
    </section>
    <section class="container p-4">
      <b-field label="Name ">
        <b-input v-model="inw.name" placeholder="Name" type="text" required>
        </b-input>
      </b-field>
      <b-field label="Img link ">
        <b-field>
          <b-input v-model="inw.lin" placeholder="URL" type="url"></b-input>
        </b-field>
      </b-field>
      <b-field label="De">
        <b-input
          type="textarea"
          minlength="10"
          maxlength="100"
          placeholder="Maxlength automatically counts characters"
          v-model="inw.area"
          required
        >
        </b-input>
      </b-field>
      <div class="level-right">
        <b-button size="is-large" @click="handleUpdateForm" class="is-dark mx-3"
          >Update</b-button
        >
        <nuxt-link to="/postlist"
          ><b-button size="is-large">Cancle</b-button></nuxt-link
        >
      </div>
    </section>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      inw: {},
    };
  },
  created() {
    let apiURL = `https://worm-57ba9-default-rtdb.firebaseio.com/post/${this.$route.params.id}.json`;
    axios.get(apiURL).then((res) => {
      this.inw = res.data;
    });
  },

  methods: {
    handleUpdateForm() {
      let apiURL = `https://worm-57ba9-default-rtdb.firebaseio.com/post/${this.$route.params.id}.json`;
      axios
        .put(apiURL, this.inw)
        .then((res) => {
          this.$buefy.notification.open({
            message: `The information has been updated successfully.`,
            type: "is-link",
            pauseOnHover: true,
          });
          this.$router.push("/postlist");
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style>
</style>