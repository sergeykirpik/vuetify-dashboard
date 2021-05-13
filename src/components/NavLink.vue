<template>
  <v-btn color="white" :to="link.url" text rounded>{{ link.label }}</v-btn>
</template>

<script>
export default {
  props: {
    link: {
      type: Object,
      required: true,
    },
  },
};
</script>