<template>
  <button
    @click="this.$emit('btn-click')"
    v-show="homePage"
    v-bind:style="{ backgroundColor: color }"
    class="btn"
  >
    {{ text }}
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    text: String,
    color: String,
  },
  computed: {
    homePage() {
      if (this.$route.path === '/') {
        return true;
      } else {
        return false;
      }
    },
  },
};
</script>
