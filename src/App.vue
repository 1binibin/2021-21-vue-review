<template>
  <div class="app-wrapper">
    <ImgCp :src="src" :title="title" />
    <ul class="thumb-wrap">
      <ThumbCp v-for="v in foods" :key="v.id" :food="v" @@change="onChange"/>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
import ImgCp from './components/ImgCp.vue';
import ThumbCp from './components/ThumbCp.vue';

export default {
  name: 'App',
  data() {
    return {
      foods: [],
      title: '',
      src: '',
    };
  },
  components: { ImgCp, ThumbCp },
  methods: {
    onChange({ title, src }) {
      this.title = title;
      this.src = src;
    },
  },
  async created() {
    const { data } = await axios.get('/json/foods.json');
    this.foods = data;
    this.title = this.foods[0].title;
    this.src = this.foods[0].src;
  },
};
</script>

<style lang="scss">
.app-wrapper {
  max-width: $wrapper-width;
  margin: 1em auto;
  .thumb-wrap {
    margin: .5em 0;
    border: 1px solid $secondary-color;
    padding: .325em;
    @include flex($jc: space-between);
  }
}
</style>
