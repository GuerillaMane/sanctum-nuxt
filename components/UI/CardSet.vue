<template>
  <div class="card-set">
    <div class="row">
      <!--      <img src="~/assets/images/work.png" alt="Card Logo">-->
      <img :src="require(`~/assets/images/${imageName}`)" alt="Card Logo">
      <a class="button-like">
        <svg width="20" height="17" viewBox="0 0 20 17" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M2.45067 9.90821L9.40329 16.4395C9.64278 16.6644 9.76253 16.7769 9.90372 16.8046C9.9673 16.8171 10.0327 16.8171 10.0963 16.8046C10.2375 16.7769 10.3572 16.6644 10.5967 16.4395L17.5493 9.90821C19.5055 8.07059 19.743 5.0466 18.0978 2.92607L17.7885 2.52734C15.8203 -0.00942016 11.8696 0.416014 10.4867 3.31365C10.2913 3.72296 9.70868 3.72296 9.51333 3.31365C8.13037 0.416014 4.17972 -0.00941634 2.21154 2.52735L1.90219 2.92607C0.256947 5.0466 0.494498 8.07059 2.45067 9.90821Z" fill="white"/>
        </svg>
      </a>
    </div>
    <h3>{{ cardText }}</h3>
  </div>
</template>

<script>
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
    }
  }
}
</script>

<style lang="scss" scoped>
.card-set {
  background: linear-gradient(45deg, rgba(154,220,255,1) 20%, rgba(255,248,154,1) 100%);
  padding: 10px;
  border-radius: 15px;
  width: 225px;
  display: flex;
  flex-direction: column;
  justify-content: start;
  align-items: start;
  gap: 15px;

  h3 {
    color: $white;
    font-weight: 600;
  }
}

.row {
  width: 100%;
  justify-content: space-between;
  align-items: start;

  img {
    height: 90px;
  }

  a {
    color: $white;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 45px;
    width: 45px;
    border-radius: 50%;
    background-color: rgba(255,255,255,0.3);

    &:hover {
      cursor: pointer;
      background-color: rgba(255,255,255,0.5);

      svg > path {
        fill: $red-pastel;
      }
    }
  }
}
</style>
