<template>
  <div class="img-wrapper">
    <img :src="src" :alt="title" class="w-100">
    <div class="title-wrap">{{ title }}</div>
  </div>
</template>

<script>
export default {
  name: 'ImgCp',
  props: ['src', 'title'],
};
</script>

<style lang="scss" scoped>
.img-wrapper {
  margin: 1em 0;
  padding: .5em;
  border: 1px solid $secondary-color;
  position: relative;
  .title-wrap {
    font-size: 2em;
    color: #dedede;
    text-align: center;
    background-color: black;
    width: calc(100% - .5em);
    @include layer($b: .325em);
  }
}
</style>
