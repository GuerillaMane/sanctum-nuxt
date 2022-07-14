<template>
  <div class="container__wrapper">
    <div class="course" v-if="course">
      <div class="course__header">
        <a class="button-round" @click="goBack">
          <svg width="8" height="14" viewBox="0 0 8 14" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M7 1L1 7L7 13" stroke="#242730" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </a>
        
        <h2>{{ course.name }}</h2>
        
        <button-like
          class="like"
          :itemId="course.slug" :is-favorite="course.isFavorite"
          @changeFavorites="changeFavorites"
        ></button-like>
      </div>

      <div class="course__detail">
        <img class="course__detail-logo" :src="require(`~/assets/images/${course.image}`)">
        <div class="course__detail-text">
          <div class="description">
            {{ course.description }}
          </div>
          <div class="pros">
            <h3>What you'll learn</h3>
            <ul>
              <li v-for="point in course.pros" :key="point">
                {{ point }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>

    <div v-else>
      Не удалось получить данные о выбранном курсе
    </div>
  </div>
</template>

<script>
import { courseList } from '../../helpers/fake-back';
import ButtonLike from '../UI/ButtonLike';

export default {
  name: 'PathCourseDetail',

  components: {
    ButtonLike
  },

  data() {
    return {
      course: null,
    };
  },

  computed: {
    id() {
      return this.$router.currentRoute.params.id;
    }
  },

  mounted() {
    this.getCourseDetail();
  },

  methods: {
    getCourseDetail() {
      this.course = courseList.find(obj => obj.slug === this.id);
    },

    goBack() {
      this.$router.go(-1);
    },

    changeFavorites() {
      this.course.isFavorite = !this.course.isFavorite;
    }
  }
}
</script>

<style lang="scss" scoped>
.course {
  width: 90%;
  margin: 30px 0;

  display: flex;
  flex-direction: column;
  gap: 45px;


  &__header{
    display: flex;
    justify-content: center;
    align-items: center;

    .button-round {
      background-color: $white;
    }

    .button-round:hover {
      svg {
        animation: left-slide .4s ease-in;
      }
    }

    h2 {
      text-align: center;
      flex-grow: 1;
    }
  }

  &__detail {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    gap: 35px;

    &-logo {
      max-width: 200px;
    }

    &-text {
      display: flex;
      flex-direction: column;
      gap: 35px;
      max-width: 500px;
      
      .description {
        text-align: justify;
        font-size: 17px;
      }

      .pros {
        h3 {
          margin-bottom: 12px;
        }

        ul {
          display: flex;
          flex-flow: row wrap;
          justify-content: space-between;

          li {
            display: inline-block;
            font-size: 14px;
            width: calc(50% - (2.4rem/2));
            margin-bottom: 12px;
          }

          li:before {
            content: '\2713';
            margin-right: 0.5em;
          }
        }
      }
    }
  }
}

.button-round.disliked::v-deep {
  svg > path {
    stroke: black;
  }
}
</style>