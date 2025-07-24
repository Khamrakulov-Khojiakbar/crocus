<template>
  <div class="app">
    <header>
      <h1>Crocus</h1>
      <p>Добро пожаловать в наш кофейник</p>
    </header>

    <section v-for="(items, category) in categorizedMenu" :key="category" class="category">
      <h2 class="category-title">{{ category }}</h2>
      <div class="grid">
        <CoffeeCard
          v-for="(item, index) in items"
          :key="index"
          :name="item.name"
          :emoji="item.emoji"
          :sizes="item.sizes"
          :popular="item.popular"
        />
      </div>
    </section>
  </div>
</template>

<script>
import CoffeeCard from './components/CoffeeCard.vue';

export default {
  components: { CoffeeCard },
  data() {
    return {
      categorizedMenu: {
        '☕ Кофе': [
    {
      name: 'Эспрессо',
      emoji: '☕️',
      sizes: [
        { name: 'Стандарт', price: 110 },
        { name: 'Двойной', price: 125 }
      ],
      popular: true
    },
    {
      name: 'Раф',
      emoji: '🥛',
      sizes: [
        { name: 'Ваниль', price: 200 },
        { name: 'Карамель', price: 200 }
      ],
      popular: true
    },
    {
      name: 'Американо',
      emoji: '☕️',
      sizes: [
        { name: 'Стандарт', price: 190 }
      ],
      popular: true
    },
    {
      name: 'Горячий шоколад',
      emoji: '🍫',
      sizes: [
        { name: 'Стандарт', price: 150 }
      ]
    },
    {
      name: 'Мокко',
      emoji: '🍫',
      sizes: [
        { name: 'Стандарт', price: 180 }
      ]
    },
    {
      name: 'Капучино',
      emoji: '☕️',
      sizes: [
        { name: 'Маленький', price: 150 },
        { name: 'Средний', price: 190 },
        { name: 'Большой', price: 240 }
      ]
    },
    {
      name: 'Латте',
      emoji: '☕️',
      sizes: [
        { name: 'Маленький', price: 150 },
        { name: 'Средний', price: 190 },
        { name: 'Большой', price: 240 }
      ]
    },
    {
      name: 'Американо',
      emoji: '☕️',
      sizes: [
        { name: 'Маленький', price: 120 },
        { name: 'Средний', price: 150 },
        { name: 'Большой', price: 200 }
      ]
    },
  ],

  'Авторские напитки ': [
    {
      name: 'Капучино Баунти',
      emoji: '🧊',
      sizes: [
        { name: 'Стандарт', price: 210 }
      ]
    },
    {
      name: 'Капучино Сникерс',
      emoji: '🧊',
      sizes: [
        { name: 'Стандарт', price: 210 }
      ]
    }
  ],

  '🍵 Чай': [
    {
      name: 'Фирменный чай CROCUS',
      emoji: '🍵',
      sizes: [
        { name: 'Стандарт', price: 250 }
      ]
    },
    {
      name: 'Ягодный чай',
      emoji: '🍵',
      sizes: [
        { name: 'Стандарт', price: 190 }
      ]
    },
    {
      name: 'Облепиховый чай',
      emoji: '🍵',
      sizes: [
        { name: 'Стандарт', price: 190 }
      ]
    },
    {
      name: 'Имбирный чай',
      emoji: '🍵',
      sizes: [
        { name: 'Стандарт', price: 190 }
      ]
    },
    {
      name: 'Клубничный чай',
      emoji: '🍵',
      sizes: [
        { name: 'Стандарт', price: 190 }
      ]
    },
    {
      name: 'Черный/Зеленый чай',
      emoji: '🍵',
      sizes: [
        { name: 'Стандарт', price: 100 }
      ]
    },
    {
      name: 'Чай',
      emoji: '🍵',
      sizes: [
        { name: 'Стакан', price: 60 }
      ]
    },
    {
      name: 'Фруктовый чай',
      emoji: '🍵',
      sizes: [
        { name: 'Стандарт', price: 110 }
      ]
    }
  ],

  'Сиропы': [
    {
      name: 'Карамель',
      emoji: '🍯',
      sizes: [
        { name: 'Дополнение', price: 30 }
      ]
    },
    {
      name: 'Ваниль',
      emoji: '🍯',
      sizes: [
        { name: 'Дополнение', price: 30 }
      ]
    },
    {
      name: 'Миндаль',
      emoji: '🍯',
      sizes: [
        { name: 'Дополнение', price: 30 }
      ]
    },
  ],

  '❄ Айс Кофе': [
    {
      name: 'Айс Латте',
      emoji: '🧊',
      sizes: [
        { name: 'Стандарт', price: 170 }
      ]
    },
    {
      name: 'Айс Американо',
      emoji: '🧊',
      sizes: [
        { name: 'Стандарт', price: 140 }
      ]
    },
    {
      name: 'Айс Капучино',
      emoji: '🧊',
      sizes: [
        { name: 'Стандарт', price: 170 }
      ]
    },
    {
      name: 'Бабл кофе',
      emoji: '🧊',
      sizes: [
        { name: 'Стандарт', price: 170 }
      ]
    },
    {
      name: 'Милкшейк клубника',
      emoji: '🧊',
      sizes: [
        { name: 'Стандарт', price: 180 }
      ]
    },
    {
      name: 'Милкшейк шоколад',
      emoji: '🧊',
      sizes: [
        { name: 'Стандарт', price: 180 }
      ]
    },
    {
      name: 'Милкшейк ваниль',
      emoji: '🧊',
      sizes: [
        { name: 'Стандарт', price: 180 }
      ]
    },
    {
      name: 'Глинтвейн вишня',
      emoji: '🧊',
      sizes: [
        { name: 'Стандарт', price: 170 }
      ]
    },
    {
      name: 'Глинтвейн яблоко',
      emoji: '🧊',
      sizes: [
        { name: 'Стандарт', price: 170 }
      ]
    }
  ],

  '🍧 FRAPPE': [
    {
      name: 'Mokko Frappe',
      emoji: '🍨',
      sizes: [
        { name: 'Стандарт', price: 170 }
      ],
      popular: true
    },
    {
      name: 'Caramel Frappe',
      emoji: '🍨',
      sizes: [
        { name: 'Стандарт', price: 170 }
      ],
      popular: true
    },
    {
      name: 'Vanilla Frappe',
      emoji: '🍨',
      sizes: [
        { name: 'Стандарт', price: 170 }
      ],
      popular: true
    },
  ],

  '🍰 Десерты': [
    {
      name: 'Брауни',
      emoji: '🍰',
      sizes: [
        { name: 'Порция', price: 200 }
      ]
    },
    {
      name: 'Чизкейк сникерс',
      emoji: '🍰',
      sizes: [
        { name: 'Порция', price: 240 }
      ]
    },
    {
      name: 'Макаронсы',
      emoji: '🍰',
      sizes: [
        { name: 'Порция', price: 200 }
      ]
    },
    {
      name: 'Мини макаронсы',
      emoji: '🍰',
      sizes: [
        { name: 'Порция', price: 130 }
      ]
    },
    {
      name: 'Пончики',
      emoji: '🍩',
      sizes: [
        { name: 'Порция', price: 90 }
      ]
    },
    {
      name: 'Пончик нутелла',
      emoji: '🍩',
      sizes: [
        { name: 'Порция', price: 110 }
      ]
    },
  ],

  'Круассан': [
    {
      name: 'Классический',
      emoji: '🥐',
      sizes: [
        { name: 'Порция', price: 140 }
      ]
    },
    {
      name: 'Шоколадный',
      emoji: '🥐',
      sizes: [
        { name: 'Порция', price: 190 }
      ]
    },
    {
      name: 'Банановый',
      emoji: '🥐',
      sizes: [
        { name: 'Порция', price: 190 }
      ]
    },
    {
      name: 'Сырный',
      emoji: '🥐',
      sizes: [
        { name: 'Порция', price: 190 }
      ]
    },
    {
      name: 'Ирис',
      emoji: '🥐',
      sizes: [
        { name: 'Порция', price: 190 }
      ]
    },
        ]
      }
    };
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap');

html, body {
  margin: 0;
  font-family: 'Poppins', sans-serif;
  color: #ffffff;
  background-color: #1c1c1c;
  background-image: url('https://images.unsplash.com/photo-1509042239860-f550ce710b93?ixlib=rb-4.0.3&auto=format&fit=crop&w=1600&q=80');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  background-attachment: fixed;
}

.app {
  max-width: 1200px;
  margin: 0 auto;
  padding: 32px 16px;
  background-color: rgba(0, 0, 0, 0.65);
  border-radius: 16px;
  box-shadow: 0 0 30px rgba(0, 0, 0, 0.7);
}

header {
  text-align: center;
  margin-bottom: 32px;
}
header h1 {
  font-size: 3rem;
  margin: 0;
  color: #ffffff;
}
header p {
  font-size: 1.1rem;
  color: #dddddd;
  margin-top: 8px;
}

.category {
  margin-bottom: 48px;
}

.category-title {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 16px;
  color: #f5c518;
  text-align: center;
  text-shadow: 0 0 6px rgba(245, 197, 24, 0.3);
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 24px;
  align-items: stretch; /* ✅ выравнивание карточек */
}

@media (max-width: 480px) {
  .app {
    padding: 24px 8px;
  }
  header h1 {
    font-size: 2.4rem;
  }
  header p {
    font-size: 1rem;
  }
  .category-title {
    font-size: 1.5rem;
  }
  .grid {
    gap: 16px;
  }
}
</style>
