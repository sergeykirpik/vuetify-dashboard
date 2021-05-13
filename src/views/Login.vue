<template>
  <v-row justify="center">
    <v-card width="400px" class="mt-10">
      <v-card-title class="pb-3">
        <h1>Login</h1>
      </v-card-title>
      <v-card-text>
        <v-form>
          <v-text-field label="Username" prepend-icon="mdi-account-circle" />
          <v-text-field
            :type="passwordFieldType"
            label="Password"
            prepend-icon="mdi-lock"
            :append-icon="passwordVisibilityIcon"
            @click:append="togglePasswordVisibility"
          />
        </v-form>
      </v-card-text>
      <v-divider></v-divider>
      <v-card-actions>
        <v-btn color="success">Register</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="info">Login</v-btn>
      </v-card-actions>
    </v-card>
  </v-row>
</template>

<script>
export default {
  data: () => ({
    showPassword: false,
  }),
  methods: {
    togglePasswordVisibility() {
      this.showPassword = !this.showPassword;
    },
  },
  computed: {
    passwordFieldType() {
      return this.showPassword ? "text" : "password";
    },
    passwordVisibilityIcon() {
      return this.showPassword ? "mdi-eye" : "mdi-eye-off";
    },
  },
};
</script>