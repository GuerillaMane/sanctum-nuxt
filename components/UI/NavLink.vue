<template>
  <div class="nav-link__fake" @mouseover="onHoverNavLink" @mouseout="onMouseOutNavLink">
    <div class="nav-link" @click="onClick">
      <a>{{ linkName }}</a>
    </div>
  </div>
</template>

<script>
import PathSearch from "../paths/PathSearch";
export default {
  name: "NavLink",
  
  components: {PathSearch},

  emits: ['onClick'],

  props: {
    linkName: {
      type: String,
      required: true
    }
  },

  methods: {
    onClick() {
      this.$emit('onClick');
    },

    changeBorders(e, value) {
      const previous = e.currentTarget.previousSibling.previousSibling;
      const next = e.currentTarget.nextSibling.nextSibling;
      if (next.className === 'nav-link__fake') {
        value ? next.style.backgroundColor = 'transparent' : next.style.backgroundColor = '#242730';
        next.firstChild.style.borderTopRightRadius = value;
      }
      if (previous.className === 'nav-link__fake') {
        value ? previous.style.backgroundColor = 'transparent' : previous.style.backgroundColor = '#242730';
        previous.firstChild.style.borderBottomRightRadius = value;
      }
      previous.style.borderBottomRightRadius = value;
      next.style.borderTopRightRadius = value;
    },

    onHoverNavLink(e) {
      this.changeBorders(e, '25px');
    },

    onMouseOutNavLink(e) {
      this.changeBorders(e, '');
    }
  }
}
</script>

<style lang="scss" scoped>
.nav-link {
  flex: 0.25;
  color: $white;
  width: 100%;
  padding: 10px;
  display: flex;
  justify-content: start;
  align-items: center;
  background-color: $bg-section;

  &:hover {
    background-color: $platinum;
    color: $black;
    cursor: pointer;
    border-top-left-radius: 25px;
    border-bottom-left-radius: 25px;
  }

  &__fake {
    width: 100%;
    background: $bg-section;
  }
}
</style>
