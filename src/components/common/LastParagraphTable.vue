<template>
  <div class="table-paragraph">
    <table>
      <tr>
        <td>
          <h1>ПРОДАВЕЦ:</h1>
          <MyParagraph>ТОО «Test»</MyParagraph>
        </td>
        <td>
          <h1>ПОКУПАТЕЛЬ:</h1>
          <MyParagraph>{{
            contractData.type === "Физическое лицо"
              ? contractData.fio
              : contractData.ulName
          }}</MyParagraph>
        </td>
      </tr>
      <tr>
        <td>
          <MyParagraph>Юр. адрес: г. Алматы, ул. Дундича д. 245</MyParagraph>
        </td>
        <td>
          <MyParagraph v-if="isFL"
            >Регистрация: {{ contractData.registred }}</MyParagraph
          >
          <br v-if="isFL" />
          <MyParagraph v-if="isFL"
            >Место жительство: {{ contractData.address }}</MyParagraph
          >
          <br v-if="isFL" />
          <MyParagraph v-if="isFL"
            >Телефон: {{ contractData.phone }}</MyParagraph
          >
          <MyParagraph v-if="!isFL">{{ contractData.address }}</MyParagraph>
          <br v-if="!isFL" />
        </td>
      </tr>
      <tr>
        <td>
          <MyParagraph>Почтовый адрес:00000</MyParagraph>
        </td>
        <td>
          <MyParagraph
            >Почтовый адрес: {{ contractData.postAddress }}</MyParagraph
          >
        </td>
      </tr>
      <tr>
        <td>
          <MyParagraph>БИН: 1111111111</MyParagraph>
        </td>
        <td>
          <MyParagraph v-if="isFL">ИИН: {{ contractData.iin }}</MyParagraph>
          <MyParagraph v-if="!isFL">БИН: {{ contractData.bin }}</MyParagraph>
        </td>
      </tr>
      <tr>
        <td>
          <MyParagraph>АО «KaspiBank»</MyParagraph><br />
          <MyParagraph>p/c: 11111111111</MyParagraph><br />
          <MyParagraph>БИК: CASPKZKA</MyParagraph><br />
        </td>
        <td>
          <MyParagraph v-if="isFL"
            >Удост. личности №:{{ contractData.idNum }}</MyParagraph
          ><br v-if="isFL" />
          <MyParagraph v-if="isFL">{{ this.idInfo }}</MyParagraph>
          <MyParagraph v-if="!isFL">{{ contractData.ulName }}</MyParagraph
          ><br v-if="!isFL" />
          <MyParagraph v-if="!isFL"
            >p/c: {{ contractData.postAddress }}</MyParagraph
          ><br v-if="!isFL" />
          <MyParagraph v-if="!isFL">БИК: {{ contractData.bik }}</MyParagraph
          ><br v-if="!isFL" />
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
import MyParagraph from "./MyParagraph.vue";

export default {
  name: "LastParagraphTable",
  components: [MyParagraph],
  data() {},
  props: {
    contractData: {},
  },
  computed: {
    isFL() {
      return this.contractData.type === "Физическое лицо";
    },
    idInfo() {
      return `Выдано когда: ${this.contractData.idGetDate}. Кем: ${this.contractData.idGetOrg}`;
    },
  },
};
</script>

<style scoped>
.table-paragraph {
  margin: 0;
  padding: 0;
  width: 100%;
}

.table-paragraph > table {
  /* border: 1px solid black; */
  width: 100%;
}

table,
th,
td {
  border: 1px solid black;
  border-collapse: collapse;
  vertical-align: top;
}

.table-paragraph > table > tr {
  /* width: 50%; */
  box-sizing: border-box;
}

h1 {
  margin: 0;
}

td {
  width: 50%;
  box-sizing: border-box;
  padding: 0px 10px;
}
</style>
