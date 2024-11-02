<template>
    <div>
      Выберите валюту:
    <select size="1" name="" id="" v-model="valuta">
      <option>₽</option>
      <option>€</option>
      <option>$</option>
    </select>
    <br><br><br>
        <div  v-for="product in products" :key="product.id">
          <p>Название продукта: {{ product.name }}</p>
          <p>Цена продукта:  {{ formattedPrice(product.price) }}</p>
          <p v-if="product.available">Статус: Available</p>
          <p v-else>Статус: Out of stock</p>
        </div>
    </div>
  </template>

<script>

export default {
  name: 'ProductDetails',
  data () {
    return {
      valuta: '',
      products: [
        {
          id: 1,
          name: 'Джинсы',
          price: 5000,
          available: true
        },
        {
          id: 2,
          name: 'Свитер',
          price: 8000,
          available: false
        },
        {
          id: 3,
          name: 'Юбка',
          price: 10000,
          available: true
        }
      ]
    }
  },
  methods: {
    formattedPrice (price) {
      switch (this.valuta) {
        case '₽':
          return `${price} рублей`
        case '€':
          return `€${(price * 0.0094).toFixed(2)}`
        case '$':
          return `$ ${(price * 0.010).toFixed(2)}`
        default:
          return price
      }
    }
  }
}
</script>

  <style lang="css" scoped>
  </style>
