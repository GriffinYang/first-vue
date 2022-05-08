<template>
  <li>
    <h2>{{ name }}{{ isFavoriated ? '(Favorite)' : '' }}</h2>
    <button @click="toggleFavorited">Toggle Favorated</button>
    <button @click="toggleDetails">
      {{ visiblity ? 'Hide' : 'Show' }} Details
    </button>
    <ul v-if="visiblity">
      <li><strong>Phone:</strong>{{ phoneNumber }}</li>
      <li><strong>Email:</strong>{{ emailAddress }}</li>
    </ul>
    <br />
    <input
      type="submit"
      value="Delete"
      class="submit"
      @click.prevent="deleteFri"
    />
  </li>
</template>
<script>
export default {
  emits: {
    'toggle-favoriate': function (id) {
      if (id) {
        return true;
      } else {
        console.warn('ID is missing!'); //Now when we use toggleFavorited incorrectlly, it send us this message
        return false;
      }
    },
  },
  props: {
    id: {
      type: String,
      required: true,
    },
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
      type: Boolean,
      required: false,
      default: false,
      //   validator: function (value) {
      //     return value === '0' || value === '1';
      //   },
    },
  },
  data() {
    return {
      visiblity: false,
      //   favoriate: this.isFavoriated,
    };
  },
  methods: {
    toggleDetails() {
      this.visiblity = !this.visiblity;
    },
    toggleFavorited() {
      //   this.favoriate = !this.favoriate;
      this.$emit('toggle-favoriate', this.id);
    },
    deleteFri() {
      this.$emit('delete-friend', this.id);
    },
  },
};
</script>
