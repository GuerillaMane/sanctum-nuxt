<template>
  <div class="main">
    <div class="container__default">
      <the-nav></the-nav>
      <Nuxt/>
    </div>
  </div>
</template>

<script>
import TheNav from "../components/layout/TheNav";

export default {
  name: "default",

  components: {
    TheNav
  }
}
</script>

<style lang="scss">
.main {
  padding: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
