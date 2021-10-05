<template>
  <li class="thumb">
    <img :src="food.src" :alt="food.title" class="w-100" @click="onChange">
  </li>
</template>

<script>
export default {
  name: 'TumbCp',
  props: ['food'],
  methods: {
    onChange(e) {
      this.$emit('@change', { src: e.target.src, alt: e.target.title });
    },
  },
};
</script>

<style lang="scss" scoped>
.thumb {
  cursor: pointer;
  margin: 1%;
  background-color: $light-color;
  img {
    opacity: .5;
    transition: opacity .75s;
    &:hover {
      opacity: 1;
    }
  }
}
</style>
