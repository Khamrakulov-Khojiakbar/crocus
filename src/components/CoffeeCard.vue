<template>
  <div 
    class="coffee-card"
    :class="{ popular }"
    @mouseenter="hover = true"
    @mouseleave="hover = false"
  >
    <div v-if="popular" class="popular-badge">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor">
        <path d="M12 2L15.09 8.26L22 9.27L17 14.14L18.18 21.02L12 17.77L5.82 21.02L7 14.14L2 9.27L8.91 8.26L12 2Z"/>
      </svg>
    </div>

    <div class="header">
      <h2 class="name">{{ name }}</h2>
      <div class="emoji">{{ emoji }}</div>
    </div>

    <div class="divider"></div>

    <ul class="sizes">
      <li v-for="size in sizes" :key="size.name">
        <span class="label">{{ size.name }}</span>
        <span class="price">{{ size.price }} сом</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'CoffeeCard',
  props: {
    name:    { type: String,  required: true },
    sizes:   { type: Array,   required: true },
     emoji:   { type: String,  default: '☕' }
  },
  data() {
    return { hover: false };
  }
};
</script>

<style scoped>
:root {
  --c-bg: #1c1c1c;
  --c-card: #2a2a2a;
  --c-dark: #ffffff;
  --c-gray: #bbbbbb;
  --c-light: #444444;
  --c-accent: #c19a6b;
  --c-popular: #c19a6b;
  --shadow-sm: 0 2px 6px rgba(0,0,0,0.2);
  --shadow-md: 0 6px 12px rgba(180, 166, 166, 0.35);
}

.coffee-card {
  position: relative;
 background: rgba(123, 118, 111, 0.336); /* более светлый и тёплый коричневый с прозрачностью */
  border-radius: 16px;
  padding: 28px 24px;
  box-shadow: var(--shadow-sm);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  border: 1px solid rgba(255,255,255,0.05);
  color: var(--c-dark);
  max-width: 360px;
  height: 80%; /* ✅ растягиваем до высоты колонки */
  display: flex;
  flex-direction: column;
  text-align: center;
}
.coffee-card:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-md);
}

.popular-badge {
  position: absolute;
  top: 16px;
  right: 16px;
  display: flex;
  align-items: center;
  gap: 6px;
  background: var(--c-popular);
  color: #fff;
  padding: 6px 12px;
  border-radius: 20px;
  font-size: 0.75rem;
  font-weight: 600;
  letter-spacing: 0.5px;
  z-index: 2;
}

.popular-badge svg {
  width: 16px;
  height: 16px;
  fill: none;
  stroke: currentColor;
  stroke-width: 2;
  stroke-linecap: round;
  stroke-linejoin: round;
}

/* Заголовок (название + emoji) */
.header {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
  margin-bottom: 1px; /* Было 12px — стало меньше */
  flex-wrap: wrap;
}

.name {
  font-weight: 250;
  font-size: 1 rem;
  color: #fff;
}

.emoji {
  font-size: 2.4rem;
}

.divider {
  width: 40px;
  height: 2px;
  background: var(--c-accent);
  margin: 1px auto; /* Было 16px — теперь меньше */
  border-radius: 2px;
  opacity: 0.9;
}

/* Размеры */
.sizes {
  list-style: none;
  padding: 0;
  margin: 20px 0 0;
}

.sizes li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0;
  border-bottom: 1px solid var(--c-light);
  font-size: 1rem;
  color: var(--c-gray);
  gap: 12px;
}

.sizes li:last-child {
  border-bottom: none;
  padding-bottom: 4px;
}

.label {
  text-transform: uppercase;
  font-size: 0.9rem;
  letter-spacing: 0.5px;
  color: #ccc;
  flex: 1;
  text-align: left;
}

.price {
  font-weight: 600;
  font-size: 1rem;
  color: var(--c-accent);
  flex-shrink: 0;
  text-align: right;
}

@media (max-width: 480px) {
  .coffee-card {
    padding: 20px 16px;
  }

  .name {
    font-size: 1.5rem;
  }

  .emoji {
    font-size: 2rem;
  }

  .label {
    font-size: 0.85rem;
  }

  .price {
    font-size: 0.95rem;
  }
}
</style>
