<template>
  <li>
    <h2>{{ name }}</h2>
    <button @click="toggleDetails">
      {{ visiblity ? 'Hide' : 'Show' }} Details
    </button>
    <ul v-if="visiblity">
      <li><strong>Phone:</strong>{{ phoneNumber }}</li>
      <li><strong>Email:</strong>{{ emailAddress }}</li>
    </ul>
  </li>
</template>
<script>
export default {
  props: ['name', 'phoneNumber', 'emailAddress'],
  data() {
    return {
      visiblity: false,
    };
  },
  methods: {
    toggleDetails() {
      this.visiblity = !this.visiblity;
    },
  },
};
</script>
