<template>
  <div class="container__sets">
    <path-search @setSearch="setSearch"></path-search>

    <h2>Course Sets</h2>
    <div class="row" v-if="courseList && courseList.length">
      <card-set
        v-for="course in courseList" :key="course.name"
        :card-text="course.name" :image-name="course.image"
        :card-color="course.cardColor" :is-favorite="course.isFavorite"
        @changeFavorites="changeFavorites" @click="getCourseDetail(course.slug)"
      ></card-set>

      <!--<card-set image-name="work.png" card-text="Engineering"></card-set>-->
      <!--<card-set image-name="books.png" card-text="Library"></card-set>-->
    </div>

    <div class="row not-found" v-else>
      <p>
        Sorry, we couldn't find any results for "{{ searchString }}"
        <br>
        <br>
        Try adjusting your search. Here are some ideas:
      </p>

      <ul>
        <li>Make sure all words are spelled correctly</li>
        <li>Try different search terms</li>
        <li>Try more general search terms</li>
      </ul>
    </div>
  </div>
</template>

<script>
import CardSet from "../../components/UI/CardSet";
import {courseList} from "../../helpers/fake-back";

export default {
  name: 'Paths',

  components: {
    CardSet,
    PathSearch: () => import('../../components/paths/PathSearch'),
  },

  data() {
    return {
      courseList: [],
      searchString: ''
    };
  },

  mounted() {
    this.getCourseList();
  },

  methods: {
    getCourseList() {
      this.courseList = courseList.map(obj => {return {...obj}});
    },

    getCourseDetail(slug) {
      // router push
    },

    changeFavorites(name) {
      const course = this.courseList.find(obj => obj.name === name);
      course.isFavorite = !course.isFavorite;
    },

    filterList() {
      this.courseList = courseList.filter(obj => {
        return obj.name.toLowerCase().includes(this.searchString.toLocaleLowerCase())
      });
    },

    setSearch(searchString) {
      if (searchString !== null) {
        this.searchString = searchString;
        this.filterList();
      }
    }
  }
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
  align-items: stretch;
  flex-wrap: wrap;

  &.not-found {
    flex-direction: column;
    align-items: start;

    p {
      font-weight: 700;
    }

    ul {
      list-style-position: inside;
    }
  }
}
</style>
