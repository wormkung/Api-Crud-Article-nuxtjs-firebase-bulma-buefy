<template>
  <div>
    <section class="hero is-dark has-text-centered">
      <div class="hero-body">
        <p class="title">Insert Data</p>
      </div>
    </section>
    <section class="container p-4  ">
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
        <b-button size="is-large" @click="onsubmit" class="is-dark mx-3"
          >Insert</b-button
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
      inw: { name: "", lin: "", area: "" },
    };
  },
  methods: {
    onsubmit(data) {
      axios
        .post(
          "https://worm-57ba9-default-rtdb.firebaseio.com/post/.json",
          this.inw
        )
        .then((res) => {
          this.$buefy.notification.open({
            message: `The information has been successfully added.`,
            type: "is-success",
            pauseOnHover: true,
          });
          this.$router.push("/postlist");
        });
    },
  },
};
</script>

<style>
</style>