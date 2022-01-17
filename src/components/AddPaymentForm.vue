<template>
  <div class="form">
    <label for="value">
      <input class="input" id="value" type="text" placeholder="Сумма" v-model="value">
    </label>
    <label for="category">
      <input class="input" id="category" type="text" placeholder="Категория" v-model="category">
    </label>
    <label for="date">
      <input class="input" id="date" type="text" placeholder="Дата" v-model="date">
    </label>
    <button class="btn" @click="addPayment">Добавить запись</button>
  </div>
</template>

<script>
export default {
  name: 'AddPaymentForm',
  data: () => ({
    value: '',
    category: '',
    date: '',
  }),
  methods: {
    addPayment() {
      if (this.value !== '' && this.category !== '') {
        const {
          value, category, date, paymentDay,
        } = this;
        const data = {
          value,
          category,
          date: date || paymentDay,
        };

        this.$emit('add-payment', data);
        this.value = '';
        this.category = '';
        this.date = '';
      }
    },
    remotePayment() {
      this.value = '';
      this.category = '';
      this.date = '';
    },
  },
  computed: {
    paymentDay() {
      const currentDate = new Date();
      const day = currentDate.getDate();
      const month = currentDate.getMonth() + 1;
      const year = currentDate.getFullYear();
      return `${day}.${month}.${year}`;
    },
  },
};
</script>

<style scoped>
.form {
  margin: 10px auto;
}
.input {
  display: flex;
  flex-wrap: wrap;
  width: 200px;
  margin: 10px auto;
  padding: 0 5px;
  border: 1px solid white;
  border-radius: 4px;
}
</style>
