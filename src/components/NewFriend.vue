<template>
  <div class="form-container">
    <form action="#" @submit.prevent="submitForm">
      <h2>Add New Friend</h2>
      <label for="name">Name:</label>
      <input type="text" name="name" v-model="name" /><br />
      <label for="phone">Phone</label>
      <input type="text" name="phone" v-model="phoneNumber" /><br />
      <label for="email">E-mail</label>
      <input type="email" name="email" v-model="emailAddress" /><br />
      <input type="submit" value="" class="submit" />
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: '',
      phoneNumber: '',
      emailAddress: '',
    };
  },
  methods: {
    submitForm() {
      this.$emit('friendAdd', this.name, this.phoneNumber, this.emailAddress);
    },
  },
};
</script>
