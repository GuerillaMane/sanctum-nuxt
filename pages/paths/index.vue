<template>
  <div class="container__sets">
    <path-search @setSearch="setSearch"></path-search>

    <h2>Course Sets</h2>
    <div class="row" v-if="courseList && courseList.length">
      <card-set
        v-for="course in courseList" :key="course.name"
        :card-text="course.name" :image-name="course.image"
        :card-color="course.cardColor"
        @changeFavorites="changeFavorites" @click.native="openCourseDetail(course.slug)"
      >
        <button-like slot="action"
          :itemId="course.slug" :is-favorite="course.isFavorite"
          @changeFavorites="changeFavorites"
        ></button-like>
      </card-set>

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
import {courseList} from "../../helpers/fake-back";
import CardSet from "../../components/UI/CardSet";
import ButtonLike from "../../components/UI/ButtonLike";

export default {
  name: 'Paths',

  components: {
    CardSet,
    PathSearch: () => import("../../components/paths/PathSearch"),
    ButtonLike
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

    openCourseDetail(id) {
      this.$router.push({path: `/paths/${id}`})
    },

    changeFavorites(id) {
      const course = this.courseList.find(obj => obj.slug === id);
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
    gap: 35px;
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
