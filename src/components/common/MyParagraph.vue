<template>
  <div class="paragraph">
    <p :style="{ textIndent: indent, paddingRight: paddingRight }">
      <slot></slot>
    </p>
  </div>
</template>

<script>
export default {
  name: "MyParagraph",
  props: {
    text: {
      type: String,
    },
    indent: {
      type: String,
      default: "0em",
    },
    paddingRight: {
      type: String,
      default: "0em",
    },
  },
};
</script>

<style scoped>
p {
  text-align: justify;
  line-height: 150%;
  margin: 0;
  padding: 0;
  /* margin-bottom: 1em; Add margin-bottom for space after the paragraph */
}
</style>
