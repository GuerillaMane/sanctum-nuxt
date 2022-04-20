<template>
  <div class="container__sets">
    <path-search></path-search>
    <h2>Course Sets</h2>
    <div class="row">
      <card-set
        card-text="Nuxt.js - Vue.js on steroids" image-name="courses/nuxt.png"
        first-color="black" second-color="rgb(154, 220, 255)"
      ></card-set>

      <card-set
        card-text="Vue 3 - The Complete Guide" image-name="courses/vue3onepiece.png"
      ></card-set>

      <!--<card-set image-name="work.png" card-text="Engineering"></card-set>-->
      <!--<card-set image-name="books.png" card-text="Library"></card-set>-->
    </div>
  </div>
</template>

<script>
import CardSet from "../../components/UI/CardSet";

export default {
  name: 'Paths',

  components: {
    CardSet,
    PathSearch: () => import('../../components/paths/PathSearch'),
  },
}
</script>

<style lang="scss" scoped>
.container {
  &__sets {
    padding: 35px;
    width: 100%;

    display: flex;
    flex-direction: column;
    gap: 25px;

    h2 {
      margin-top: 10px;
      font-weight: 700;
      font-size: 22px;
      line-height: 140%;
      color: $black;
    }
  }
}

.row {
  gap: 25px;
  justify-content: start;
}
</style>
