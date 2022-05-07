<template>
  <li>
    <h2>{{ friend.name }}</h2>
    <button @click="toggleDetails">
      {{ visibility ? 'Hide' : 'Show' }} Details
    </button>
    <ul v-if="visiblity">
      <li><strong>Phone:</strong>{{ friend.phone }}</li>
      <li><strong>Email:</strong>{{ friend.email }}</li>
    </ul>
  </li>
</template>
<script>
export default {
  data() {
    return {
      visiblity: false,
      friend: {
        id: 'manuel',
        name: 'Manuel Lorenz',
        phone: '17764484851',
        email: 'manuel@gmail.com',
      },
    };
  },
  methods: {
    toggleDetails() {
      this.visiblity = !this.visiblity;
    },
  },
};
</script>
