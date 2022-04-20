<template>
  <div class="container__sets">
    <h2>Course Sets</h2>
    <div class="row">
      <card-set image-name="work.png" card-text="Engineering"></card-set>
      <card-set image-name="books.png" card-text="Library"></card-set>
    </div>
  </div>
</template>

<script>
import CardSet from "../../components/UI/CardSet";

export default {
  name: 'Paths',

  components: {
    CardSet
  },
}
</script>

<style lang="scss" scoped>
.container {
  &__sets {
    padding: 35px;
    display: flex;
    flex-direction: column;

    gap: 25px;

    h2 {
      font-weight: 700;
      font-size: 22px;
      line-height: 140%;
      color: $black;
    }
  }
}

.row {
  gap: 25px;
}
</style>
