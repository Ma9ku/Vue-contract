<template>
  <div id="contractInputs">
    <div class="wrapper">
      <div class="input-row">
        <label for="firstInput">Дата</label>
        <input
          type="date"
          id="start"
          name="trip-start"
          v-model="date"
          @input="emitDate(date)"
        />
      </div>
      <div class="input-row">
        <label for="data_1">Дополнительные услуги</label>
        <input
          type="text"
          placeholder="по замеру помещения, установке (монтажу) и доставке Товара"
          v-model="data_1"
          name="data_1"
          id="data_1"
          @input="emitData('data_1', data_1)"
        />
      </div>
      <div class="input-row">
        <label for="data_2">Размер предоплаты</label>
        <input
          type="number"
          v-model="data_2"
          name="data_2"
          id="data_2"
          @input="emitData('data_2', data_2)"
        />
      </div>
      <div class="input-row">
        <label for="selectOption">Тип субъекта</label>
        <select
          id="selectOption"
          v-model="selectedOption"
          @change="emitTypeSelection(selectedOption)"
        >
          <option value="Юридическое лицо">Юридическое лицо</option>
          <option value="Физическое лицо">Физическое лицо</option>
        </select>
      </div>
      <!-- {{ firstInput }} -->
      <div class="input-row" v-if="isFL">
        <label for="fio">ФИО</label>
        <input
          type="text"
          v-model="fio"
          name="fio"
          id="fio"
          @input="emitData('fio', fio)"
        />
      </div>
      <div class="input-row" v-if="isFL">
        <label for="idNum">№ уд. личности</label>
        <input
          type="text"
          v-model="idNum"
          name="idNum"
          id="idNum"
          @input="emitData('idNum', idNum)"
        />
      </div>
      <div class="input-row" v-if="isFL">
        <label for="iin">ИИН</label>
        <input
          type="text"
          v-model="iin"
          name="iin"
          id="iin"
          @input="emitData('iin', iin)"
        />
      </div>
      <div class="input-row" v-if="isFL">
        <label for="idGetOrg">Выдан</label>
        <input
          type="text"
          v-model="idGetOrg"
          name="idGetOrg"
          id="idGetOrg"
          @input="emitData('idGetOrg', idGetOrg)"
        />
      </div>
      <div class="input-row" v-if="isFL">
        <label for="idGetDate">Дата выдачи</label>
        <!-- <input
          type="text"
          v-model="idGetDate"
          name="idGetDate"
          id="idGetDate"
          @input="emitData('idGetDate', idGetDate)"
        /> -->
        <input
          type="date"
          id="idGetDate"
          name="idGetDate"
          v-model="idGetDate"
          @input="emitIdGetDateChanged(date)"
        />
      </div>
      <div class="input-row" v-if="!isFL">
        <label for="ulName">Название компании</label>
        <input
          type="text"
          v-model="ulName"
          name="ulName"
          id="ulName"
          @input="emitData('ulName', ulName)"
        />
      </div>
      <div class="input-row" v-if="!isFL">
        <label for="directorName">ФИО директора</label>
        <input
          type="text"
          v-model="directorName"
          name="directorName"
          id="directorName"
          @input="emitData('directorName', directorName)"
        />
      </div>
      <div class="input-row" v-if="!isFL">
        <label for="bin">БИН</label>
        <input
          type="text"
          v-model="bin"
          name="bin"
          id="bin"
          @input="emitData('bin', bin)"
        />
      </div>
      <div class="input-row">
        <label for="address">Адрес</label>
        <input
          type="text"
          v-model="address"
          name="address"
          id="address"
          @input="emitData('address', address)"
        />
      </div>
      <div class="input-row" v-if="isFL">
        <label for="registred">Регистрация</label>
        <input
          type="text"
          v-model="registred"
          name="registred"
          id="registred"
          @input="emitData('registred', registred)"
        />
      </div>
      <div class="input-row" v-if="isFL">
        <label for="phone">Телефон</label>
        <input
          type="text"
          v-model="phone"
          name="phone"
          id="phone"
          @input="emitData('phone', phone)"
        />
      </div>
      <div class="input-row">
        <label for="postAddress">Почтовый адрес</label>
        <input
          type="text"
          v-model="postAddress"
          name="postAddress"
          id="postAddress"
          @input="emitData('postAddress', postAddress)"
        />
      </div>
      <div class="input-row" v-if="!isFL">
        <label for="bik">БИК</label>
        <input
          type="text"
          v-model="bik"
          name="bik"
          id="bik"
          @input="emitData('bik', bik)"
        />
      </div>
      <div class="save" @click="emitSaveData">Сохранить</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ContractInputs",
  data() {
    return {
      date: new Date(),
      data_1: "",
      data_2: "",
      selectedOption: "Физическое лицо",
      fio: "",
      idNum: "",
      idGetOrg: "",
      idGetDate: new Date(),
      ulName: "",
      directorName: "",
      address: "",
      registred: "",
      bin: "",
      phone: "",
      postAddress: "",
      bik: "",
    };
  },
  methods: {
    emitData(name, value) {
      this.$emit("dataChanged", { name, value });
    },
    emitDate(date) {
      this.$emit("dateChanged", { date });
    },
    emitTypeSelection(selectedOption) {
      this.$emit("typeSelected", { selectedOption });
    },
    emitIdGetDateChanged(date) {
      this.$emit("idGetDateChanged", { date });
    },
    emitSaveData() {
      this.$emit("onSave");
    },
  },
  computed: {
    isFL() {
      return this.selectedOption === "Физическое лицо";
    },
  },
};
</script>

<style>
#contractInputs {
  padding-top: 50px;
  max-width: 40%;
  min-width: 400px;
  border-left: 1px solid black;
  border-right: 1px solid black;

  display: flex;
  flex-direction: column;
  gap: 20px;
}

.wrapper {
  display: inherit;
  flex-direction: inherit;
  gap: inherit;
  padding: 10px 20px;
}

.input-row {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  /* align-items: center; */
  gap: 10px;
}

.input-row > label {
  width: 120px;
  box-sizing: border-box;
}

.input-row > input,
select {
  width: 250px;
  box-sizing: border-box;
}

input,
select {
  /* width: 400px; */
  height: 1.5rem;
  border: 1px solid black;
  border-radius: 2px;
  outline: none;
  padding: 2px 5px;

  font-size: 1.1rem;
}

.save {
  /* width: 200px; */
  width: max-content;
  padding: 10px;
  background-color: rgb(159, 220, 178);
  color: black;
  text-align: center;
  border-radius: 4px;
  cursor: pointer;
}
</style>
