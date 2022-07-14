<template>
  <div class="card-set" :style="cssProps">
    <div class="row">
      <img :src="require(`~/assets/images/${imageName}`)" alt="Card Logo">
      <slot name="action"></slot>
    </div>
    <h3>{{ cardText }}</h3>
  </div>
</template>

<script>
import {colors} from "../../helpers/card-colors";

export default {
  name: "CardSet",

  props: {
    imageName: {
      type: String,
      required: true
    },
    cardText: {
      type: String,
      required: true
    },
    cardColor: {
      type: String,
      required: true
    }
  },

  computed: {
    cssProps() {
      return {
        '--background-card': `linear-gradient(45deg, black 20%, ${colors[this.cardColor]} 100%)`
      };
    }
  },
}
</script>

<style lang="scss" scoped>
.card-set {
  background: var(--background-card);
  padding: 10px;
  border-radius: 15px;
  width: 225px;
  min-height: 190px;
  display: flex;
  flex-direction: column;
  justify-content: start;
  gap: 15px;

  &:hover {
    cursor: pointer;
    box-shadow: 1px 2px 3px 4px rgba(20,20,20,0.4);}

  h3 {
    color: $white;
    font-weight: 600;
    margin-top: auto
  }
}

.row {
  width: 100%;
  justify-content: space-between;
  align-items: start;

  img {
    max-width: 120px;
    max-height: 90px;
  }
}
</style>
