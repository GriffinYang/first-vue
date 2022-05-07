<template>
  <li>
    <h2>{{ name }}{{}}</h2>
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
  props: {
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
    },
    isFavoriated: {
      type: String,
      required: false,
      default: '0',
      validator: function (value) {
        return value === '0' || value === '1';
      },
    },
  },
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
