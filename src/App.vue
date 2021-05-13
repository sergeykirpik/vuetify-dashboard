<template>
  <v-app>
    <NavBar :links="links" />
    <v-main>
      <router-view />
    </v-main>
    <Footer :links="links" />
  </v-app>
</template>

<script>
import Footer from "./components/Footer.vue";
import NavBar from "./components/NavBar.vue";
export default {
  name: "App",

  components: { NavBar, Footer },

  data: () => ({
    links: [
      {
        label: "Home",
        url: "/",
      },
      {
        label: "Login",
        url: "/login",
      },
      {
        label: "Dashboard",
        url: "/dashboard",
      },
    ],
  }),
};
</script>
