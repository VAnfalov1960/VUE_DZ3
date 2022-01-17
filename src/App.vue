<template>
  <div id="app">
    <header>
      <h1 class="header">Персональный калькулятор</h1>
    </header>
    <main class="main">
      <button class="btn" @click="addRemoteForm">
        <p v-show="!show">Показать форму</p>
        <p v-show="show">Cкрыть форму</p>
      </button>
      <AddPaymentForm v-show="show" @add-payment="addPayment"/>
      <h3>Мои расходы:</h3>
      <PaymentDisplay :items="paymentsList"/>
    </main>
  </div>
</template>

<script>
import PaymentDisplay from '@/components/PaymentDisplay.vue';
import AddPaymentForm from '@/components/AddPaymentForm.vue';

export default {
  name: 'App',
  components: {
    AddPaymentForm,
    PaymentDisplay,
  },
  data: () => ({
    show: false,
    paymentsList: [],
  }),
  methods: {
    addRemoteForm() {
      this.show = !this.show;
    },
    fetchData() {
      return [
        {
          date: '1.1.2022',
          category: 'Подарки',
          value: 5000,
        },
        {
          date: '2.1.2022',
          category: 'Развлечения',
          value: 3000,
        },
        {
          date: '3.1.2022',
          category: 'Театр',
          value: 1500,
        },
      ];
    },
    addPayment(data) {
      this.paymentsList.push(data);
    },
  },
  created() {
    this.paymentsList = this.fetchData();
  },
};
</script>

<style>
* {
  margin: 0;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  /* -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale; */
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.main {
  display: relative;
  width: 700px;
  min-height: 250px;
  margin: 10px auto;
  padding: 10px;
  background-color: blue;
  border: 1px solid white;
  border-radius: 10px;
  color: white;
}
.btn {
  width: 208px;
  height: 50px;
  margin: 10px auto;
  border: 1px solid white;
  border-radius: 10px;
  background-color: rgb(29, 236, 29);
}
.btn:hover {
  cursor: pointer;
  background-color: green;
  color: white;
}
</style>
