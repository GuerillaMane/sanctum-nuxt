<template>
  <div class="nav-fake">
    <div class="nav-fake__column"></div>
    <nav class="nav">
      <div class="nav-header">
        <img :src="require('~/assets/images/3311275.png')" alt="App Icon">
        <h2>Sanctum</h2>
      </div>

      <nav-link link-name="Home" @onClick="$router.push('/')"></nav-link>
      <nav-link link-name="Learning paths" @onClick="$router.push('/paths')"></nav-link>

      <div class="nav-footer">
        <p>&copy; 2022</p>
      </div>
    </nav>
  </div>
</template>

<script>
import NavLink from "../UI/NavLink";

export default {
  name: "TheNav",

  components: {
    NavLink
  }
}
</script>

<style lang="scss" scoped>
.nav {
  flex: 5;
  height: 100%;
  //box-shadow: 5px 0 5px -5px rgba(0,0,0,0.75);

  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;

  &-header {
    flex: 3;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 7px;

    width: 100%;
    background-color: $bg-section;
    border-top-right-radius: 25px;

    h2 {
      color: $white;
      margin-right: 15px;
    }

    img {
      height: 4rem;
      margin-right: 15px;
    }
  }

  &-footer {
    flex: 2;
    width: 100%;
    background-color: $bg-section;
    border-bottom-right-radius: 25px;
    display: flex;
    justify-content: center;
    align-items: center;

    p {
      color: $white;
      margin-right: 15px;
    }
  }
}

.nav-fake {
  flex: 1;
  border-radius: 25px;
  background-color: $platinum;
  max-width: 160px;

  display: flex;
  flex-direction: row;

  &__column {
    flex: 1;
    background-color: $bg-section;
    border-top-left-radius: 25px;
    border-bottom-left-radius: 25px;
  }
}
</style>
