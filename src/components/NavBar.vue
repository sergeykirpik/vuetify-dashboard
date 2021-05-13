<template>
  <v-app-bar dark app color="primary">
    <v-toolbar-title>Vuetify Dashboard</v-toolbar-title>
    <v-spacer></v-spacer>
    <NavLink v-for="link in links" :key="link.url" :link="link" />
  </v-app-bar>
</template>

<script>
import NavLink from "@/components/NavLink.vue";
export default {
  components: {
    NavLink,
  },
  props: {
    links: Array,
  },
};
</script>