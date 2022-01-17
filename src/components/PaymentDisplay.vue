<template>
  <div>
    <div class="display" v-for="(item, index) in items"
      :key="index">
      {{index+1}}. {{item.date}}, Расход: {{item.category}}, Сумма: {{item.value}} рублей.</div>
  </div>
</template>

<script>
export default {
  name: 'PaymentDisplay',
  props: {
    items: {
      type: Array,
      default: () => ([]),
    },
    show: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style scoped>
.display {
  padding-left: 50px;
  text-align: left;
}
</style>
