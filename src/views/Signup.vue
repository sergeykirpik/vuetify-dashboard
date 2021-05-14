<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Signup Page</h1>
        <v-form ref="signupForm" v-model="formValidity">
          <v-text-field
            label="Email"
            type="email"
            v-model="email"
            :rules="emailRules"
          />
          <v-autocomplete label="Which browser do you use?" :items="browsers" />
          <v-file-input label="Attach profile picture" />
          <v-text-field label="Birthday" v-model="birthday" readonly />
          <v-row class="mb-5">
            <v-date-picker
              header-color="green"
              v-model="birthday"
              class="mt-5"
            />
          </v-row>
          <v-checkbox
            label="Agree to terms & conditions"
            v-model="agreeToTerms"
            :rules="agreeToTermsRules"
            required
          />
          <v-btn
            type="submit"
            color="primary"
            class="mr-4"
            :disabled="!formValidity"
            >Submit</v-btn
          >
          <v-btn color="success" class="mr-4" @click="validateForm"
            >Validate Form</v-btn
          >
          <v-btn color="warning" class="mr-4" @click="resetValidation"
            >Reset Validation</v-btn
          >
          <v-btn color="error" @click="resetForm">Reset</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  methods: {
    validateForm() {
      this.$refs.signupForm.validate();
    },
    resetValidation() {
      this.$refs.signupForm.resetValidation();
    },
    resetForm() {
      this.$refs.signupForm.reset();
    },
  },
  data: () => ({
    browsers: ["Chrome", "Firefox", "Safari", "Edge", "Brave"],
    birthday: "",
    agreeToTerms: false,
    agreeToTermsRules: [
      (value) =>
        !!value ||
        "You must agree to the terms and conditions to sign up for account.",
    ],
    email: "",
    emailRules: [
      (value) => value.indexOf("@") !== 0 || "Email should have a username",
      (value) => value.includes("@") || "Email should include an @ symbol.",
      (value) =>
        value.indexOf(".") - value.indexOf("@") > 1 ||
        "Email should contain a valid domain",
      (value) => value.includes(".") || "Email should include a period symbol.",
      (value) =>
        value.indexOf(".") <= value.length - 3 ||
        "Email should contain a valid domain extension.",
    ],
    formValidity: false,
  }),
};
</script>