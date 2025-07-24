<template>
  <div class="menu-container">
    <div v-for="(items, category) in groupedMenu" :key="category" class="category-section">
      <h2 class="category-title">{{ formatCategory(category) }}</h2>
      <div class="cards-wrapper">
        <CoffeeCard
          v-for="item in items"
          :key="item.name"
          :name="item.name"
          :sizes="item.sizes"
          :emoji="item.emoji"
          :popular="item.popular"
        />
      </div>
    </div>
  </div>
</template>

<script>
import CoffeeCard from './CoffeeCard.vue';

export default {
  components: { CoffeeCard },
  data() {
    return {
      menuItems: [
        { type: 'coffee', name: 'Капучино', emoji: '☕', popular: true, sizes: [{ name: 'мал.', price: 120 }, { name: 'сред.', price: 140 }] },
        { type: 'tea', name: 'Чёрный чай', emoji: '🍵', sizes: [{ name: '1 чашка', price: 80 }] },
        { type: 'ice-coffee', name: 'Айс Латте', emoji: '🧊☕', sizes: [{ name: '350 мл', price: 150 }] },
        { type: 'frappe', name: 'Фраппе ванильный', emoji: '🥤', sizes: [{ name: '400 мл', price: 180 }] },
        { type: 'lemonade', name: 'Лимонад клубника', emoji: '🍓🥤', sizes: [{ name: '500 мл', price: 160 }] },
        { type: 'dessert', name: 'Чизкейк', emoji: '🍰', sizes: [{ name: 'порция', price: 200 }] },
        // Добавьте другие товары
      ]
    };
  },
  computed: {
    groupedMenu() {
      return this.menuItems.reduce((acc, item) => {
        if (!acc[item.type]) acc[item.type] = [];
        acc[item.type].push(item);
        return acc;
      }, {});
    }
  },
  methods: {
    formatCategory(type) {
      const map = {
        coffee: '☕ Кофе',
        tea: '🍵 Чай',
        'ice-coffee': '🧊 Айс Кофе',
        frappe: '🥤 Фраппе',
        lemonade: '🍋 Лимонады',
        dessert: '🍰 Десерты'
      };
      return map[type] || type;
    }
  }
};
</script>

<style scoped>
.menu-container {
  display: flex;
  flex-direction: column;
  gap: 48px;
  padding: 32px 16px;
  max-width: 1200px;
  margin: 0 auto;
}

.category-section {
  width: 100%;
}

.category-title {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 20px;
  color: #fff;
  border-bottom: 2px solid var(--c-accent);
  display: inline-block;
  padding-bottom: 4px;
}

.cards-wrapper {
  display: flex;
  flex-wrap: wrap;
  gap: 24px;
}
</style>
