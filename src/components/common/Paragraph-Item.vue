<template>
  <div class="paragraph-item">
    <h1>{{ itemNum }}.{{ header }}</h1>
    <MyParagraph indent="2em" v-for="(item, index) in list" :key="index">
      {{ itemNum }}.{{ index + 1 }}. {{ item }}
    </MyParagraph>
  </div>
</template>

<script>
import MyParagraph from "./MyParagraph.vue";

export default {
  components: {
    MyParagraph,
    // MyParagraph
  },
  props: {
    header: {
      type: String,
      required: true,
    },
    list: {
      type: Array,
    },
    itemNum: {
      type: Number,
    },
  },
};
</script>

<style scoped>
h1 {
  font-size: 1rem;
  font-weight: bold;
  width: 100%;
  text-align: center;
  text-transform: uppercase;
  margin: 0;
  margin-bottom: 0px;
}

.paragraph-item {
  margin-bottom: 15px;
}
</style>
