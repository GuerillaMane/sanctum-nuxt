<template>
  <path-course-detail
    :id="courseId"
  ></path-course-detail>
</template>

<script>
export default {
  name: "index",

  components: {
    PathCourseDetail: () => import('../../../components/paths/PathCourseDetail.vue')
  },

  computed: {
    courseId() {
      this.$router.currentRoute.params.id;
    }
  },
}
</script>

<style scoped>

</style>
