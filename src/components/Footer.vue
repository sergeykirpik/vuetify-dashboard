<template>
  <v-footer color="primary lighten-1" padless>
    <v-row justify="center" no-gutters>
      <NavLink
        v-for="link in links"
        :key="link.url"
        :link="link"
        class="my-2"
      />

      <v-col class="primary lighten-2 py-4 text-center white--text" cols="12">
        {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      </v-col>
    </v-row>
  </v-footer>
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