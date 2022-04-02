<template>
  <div class="w-full md:flex md:justify-center mb-6">
    <div class="m-12 w-1/2">
      <h1 class="text-4xl mb-8">Social-Influenza</h1>
      <Error :error="error" v-if="error" class="mb-2" />
      <Success :message="message" v-if="message" class="mb-2" />
      <FormInput
        label="First Name"
        type="text"
        :form="form"
        field="first_name"
      />
      <FormInput label="Last Name" type="text" :form="form" field="last_name" />
      <FormInput
        label="Email Address"
        type="email"
        :form="form"
        field="email"
      />
      <FormInput
        label="Phone Number"
        type="number"
        :form="form"
        field="phone"
      />
      <FormInput
        label="Twitter Handle"
        type="text"
        :form="form"
        field="twitter_handle"
      />
      <FormInput
        label="Instagram Handle"
        type="text"
        :form="form"
        field="instagram_handle"
      />
      <FormInput
        label="Password"
        type="password"
        :form="form"
        field="password"
      />
      <FormInput
        label="Confirm Password"
        type="password"
        :form="form"
        field="confirm_password"
      />
      <FormButton :label="loading" :submit="submit" />
    </div>
  </div>
</template>

<script>
export default {
  name: "Register",
  data() {
    return {
      form: {
        first_name: "",
        last_name: "",
        email: "",
        phone: "",
        twitter_handle: "",
        instagram_handle: "",
        password: "",
        confirm_password: "",
      },
      loading: "Register Now",
      error: null,
      message: null,
    };
  },
  methods: {
    async submit() {
      this.loading = "Requesting.....";
      this.error = null;
      this.message = null;
      try {
        const response = await this.$axios.post(
          "api/register-account",
          this.form
        );
        const data = response.data;
        if (data.status == "successful") {
          this.message = data.message;
        } else {
          this.error = data.message;
        }
        this.loading = "Register Now";
      } catch (ex) {
        this.error = ex.response.data.message;
        this.loading = "Register Now";
      }
    },
  },
};
</script>
