<template>
  <footer>
    <div class="container">
      <router-link class="logo-font" :to="{ name: 'home', params: {} }">
        程序员社区
      </router-link>
    </div>
  </footer>
</template>

<script>
export default {
  name: "RwvFooter"
};
</script>
