<template>
  <fragment>
    <div>
      <router-link :exact="true" to="/">Home</router-link>
      {{ ' | ' }}
      <router-link to="/about">About</router-link>
      <fragment v-if="isAuth">
        {{ ' | ' }}
        <router-link to="/user">User</router-link>
        {{ ' | ' }}
        <router-link to="/search">Search</router-link>
        {{ ' | ' }}
        <router-link to="/chart">Chart</router-link>
        {{ ' | ' }}
        <router-link to="/i18n">I18N</router-link>
        {{ ' | ' }}
        <router-link to="/movie">Movie</router-link>
        {{ ' | ' }}
        <router-link to="/form">Form</router-link>
        {{ ' | ' }}
        <router-link to="/nested">Nested</router-link>
        {{ ' | ' }}
        <router-link to="/pagination">Pagination</router-link>
      </fragment>
      {{ ' | ' }}
      <a v-if="!isAuth" v-on:click="login()" href="#">Login</a>
      <a v-else v-on:click="logout()" href="#">Logout</a>
    </div>
  </fragment>
</template>
<script>
import axios from "axios";

const url = "https://untitled-ykhxk39uvzy3.runkit.sh/login";

export default {
  mounted() {
    const token = localStorage.getItem("token");

    if (token) {
      this.isAuth = true;
    }
  },
  data() {
    return {
      isAuth: false
    };
  },
  methods: {
    async login() {
      try {
        const { data } = await axios.post(url, {});
        const { token } = data;

        localStorage.setItem("token", token);
        console.log(data);
        this.isAuth = true;
      } catch (e) {
        console.log("err", e.message);
        this.isAuth = false;
      }
    },
    async logout() {
      try {
        localStorage.removeItem("token");
        this.isAuth = false;
        this.$router.push("/");
      } catch (e) {
        console.log("err", e.message);
      }
    }
  }
};
</script>