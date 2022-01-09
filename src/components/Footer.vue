<template>
  <footer>
    <p>
      Copyright &copy; {{ year }}. All rights reserved. Design by Emmanuel
      Adebayo&trade;
    </p>
    <router-link to="/about">About</router-link>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  computed: {
    year() {
      return new Date().getFullYear();
    },
  },
};
</script>

<style scoped>
a:link,
a:active {
  color: #333;
  text-decoration: none;
}

footer {
  margin-top: 30px;
  text-align: center;
}
</style>
