<template>
  <div class="contract">
    <h1>{{ header }}</h1>
    <div class="sub-header">
      <div class="city">
        <MyParagraph indent="1em">{{ city }}</MyParagraph>
      </div>
      <div class="date">
        <MyParagraph paddingRight="1em">{{ date }}</MyParagraph>
      </div>
    </div>
    <div class="contractCase" v-html="contractCase"></div>
    <div v-for="(paragraph, index) in paragraphItems" :key="index">
      <ParagraphItem
        :header="paragraph.title"
        :itemNum="index + 1"
        :list="paragraph.items"
      />
    </div>
    <LastParagraphTable :contractData="contractData" />
  </div>
</template>

<script>
import MyParagraph from "./common/MyParagraph.vue";
import ParagraphItem from "./common/Paragraph-Item.vue";
import LastParagraphTable from "./common/LastParagraphTable.vue";
// import MyParagraph from "./common/MyParagraph.vue";

export default {
  components: {
    MyParagraph,
    ParagraphItem,
    LastParagraphTable,
    // MyParagraph
  },
  data() {
    return {
      paragraphText: "This is some sample text.",
    };
  },
  props: {
    header: {
      type: String,
      required: true,
    },
    city: {
      type: String,
    },
    contractCase: {
      type: String,
      required: true,
    },
    date: {
      type: String,
    },
    paragraphItems: {
      type: Array,
    },
    contractData: {},
  },
};
</script>

<style>
.contract {
  max-width: 600px;
  min-width: 500px;
  border-left: 1px solid black;
  border-right: 1px solid black;
  height: 100%;

  font-family: "Times New Roman", Times, serif;
  font-size: 12px;

  padding: 40px 30px 40px 50px;
}

h1 {
  width: 100%;
  text-align: center;
  font-size: 1rem;
  /* margin: 0 auto; */
}

.sub-header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;

  margin-bottom: 15px;
}

.contractCase {
  text-align: justify;
  line-height: 150%;

  margin-bottom: 15px;
  padding: 0; /* Reset padding for the entire paragraph */
  text-indent: 2em;
}
</style>
