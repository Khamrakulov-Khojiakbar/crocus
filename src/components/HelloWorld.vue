<!-- CoffeeMenu.vue -->
<template>
  <div class="menu">
    <h1>Меню кофейни ☕</h1>
    <div v-for="item in items" :key="item.name" class="coffee-item">
      <h2>{{ item.name }}</h2>
      <ul>
        <li v-for="size in item.sizes" :key="size.name">
          {{ size.name }} — {{ size.price }} сом
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CoffeeMenu',
  props: {
    items: {
      type: Array,
      required: true
    }
  }
};
</script>

<style scoped>
.menu {
  padding: 20px;
  font-family: sans-serif;
}
.coffee-item {
  margin-bottom: 20px;
}
h1 {
  color: #6b4f4f;
}
h2 {
  margin-bottom: 5px;
}
ul {
  padding-left: 15px;
}
li {
  list-style: none;
}
</style>