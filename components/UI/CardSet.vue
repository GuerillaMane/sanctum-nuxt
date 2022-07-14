<template>
  <div class="card-set" :style="cssProps">
    <div class="row">
      <img :src="require(`~/assets/images/${imageName}`)" alt="Card Logo">
      <a
        class="button-round" :class="[isFavorite ? 'liked' : 'disliked']"
        @click="changeFavorites"
      >
        <svg width="20" height="17" viewBox="0 0 20 17" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path
            d="M2.45067 9.90821L9.40329 16.4395C9.64278 16.6644 9.76253 16.7769 9.90372 16.8046C9.9673 16.8171 10.0327 16.8171 10.0963 16.8046C10.2375 16.7769 10.3572 16.6644 10.5967 16.4395L17.5493 9.90821C19.5055 8.07059 19.743 5.0466 18.0978 2.92607L17.7885 2.52734C15.8203 -0.00942016 11.8696 0.416014 10.4867 3.31365C10.2913 3.72296 9.70868 3.72296 9.51333 3.31365C8.13037 0.416014 4.17972 -0.00941634 2.21154 2.52735L1.90219 2.92607C0.256947 5.0466 0.494498 8.07059 2.45067 9.90821Z"
            fill="white"/>
        </svg>
      </a>
    </div>
    <h3>{{ cardText }}</h3>
  </div>
</template>

<script>
import {colors} from "../../helpers/card-colors";

export default {
  name: "CardSet",

  emits: ['changeFavorites'],

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
    },
    isFavorite: {
      type: Boolean,
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

  methods: {
    changeFavorites() {
      this.$emit('changeFavorites', this.cardText);
    }
  }
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

.button-round {
  background-color: rgba(255, 255, 255, 0.3);

  &.liked {
    svg > path {
      fill: $red-pastel;
    }
  }

  &:hover {
    background-color: rgba(255, 255, 255, 0.5);

    //&.disliked {
    //  svg > path {
    //    fill: $red-pastel;
    //  }
    //}
    //
    //&.liked {
    //  svg > path {
    //    fill: $white;
    //  }
    //}
  }
}
</style>
