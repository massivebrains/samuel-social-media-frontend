<template>
  <div class="w-full md:flex md:justify-center mb-6">
    <div class="m-12 w-1/2">
      <h1 class="text-4xl mb-8">Social-Influenza</h1>
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
        field="password_confirmation"
      />
      <FormButton label="Register Now" :submit="submit" />
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
        password_confirmation: "",
      },
    };
  },
  methods: {
    submit() {
      alert(JSON.stringify(this.form));
    },
  },
};
</script>
