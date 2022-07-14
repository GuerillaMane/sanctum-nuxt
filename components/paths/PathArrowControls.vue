<template>
  <div class="controls">
    <a class="button-round left">
      <svg width="8" height="14" viewBox="0 0 8 14" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M7 1L1 7L7 13" stroke="#959BA5" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </a>
    <a class="button-round right">
      <svg width="8" height="14" viewBox="0 0 8 14" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M1 1L7 7L1 13" stroke="#242730" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </a>
  </div>
</template>

<script>
export default {
  name: "PathArrowControls"
}
</script>

<style lang="scss" scoped>
.button-round {
  background-color: transparent;

  &.left:hover {
    svg {
      animation: left-slide .4s ease-in;
    }
  }

  &.right:hover {
    svg {
      animation: right-slide .4s ease-in;
    }
  }
}
</style>
