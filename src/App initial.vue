<template>
  <main>
    <ul class="grid">
      <template v-for="item in items" :key="item.id">
        <li :id="item.id" class="cui-p-m">
          <p>{{ item.id }}</p>
          <button type="button" data-quick-view @click="toggleQuickView(item.id)">
            Quick view
          </button>
        </li>
        <li :id="`quickview-${item.id}`" :class="['fullwidth', { 'is-hidden': !item.isOpen }]">
          <button type="button" data-close @click="toggleQuickView(item.id)">
            Close {{ item.id }}
          </button>
          <p>fullwidth {{ item.id }}</p>
          <p>
            This grid item should take up the entire width of the screen and shift the other items
            below it, ensuring a smooth flow while maintaining connection with the previous item.
          </p>
          <p>
            Test
            <a href="#">inline link</a>
            .
          </p>
        </li>
      </template>
    </ul>
  </main>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'QuickViewGrid',
  setup() {
    const items = ref(
      Array.from({ length: 20 }, (_, i) => ({
        id: i + 1,
        isOpen: false,
      })),
    )

    const toggleQuickView = (id) => {
      items.value = items.value.map((item) =>
        item.id === id ? { ...item, isOpen: !item.isOpen } : { ...item, isOpen: false },
      )
    }

    return { items, toggleQuickView }
  },
}
</script>

<style scoped>
.grid {
  display: grid;
  gap: 16px;
  grid-auto-flow: dense;
  grid-template-columns: repeat(3, 120px);
  justify-content: center;
  padding: 16px;
}

.grid > * {
  align-items: flex-start;
  background: #eee;
  display: flex;
  flex-direction: column;
  min-height: 100px;
  padding: 16px;
}

.fullwidth {
  grid-column: 1 / -1;
}

.is-hidden {
  display: none;
}

.fullwidth,
.is-selected {
  color: black;
  background: #ccc;
}

/* Buttons */

button[data-quick-view] {
  background-color: #007bff;
  color: white;
  font-size: 16px;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition:
    background-color 0.3s ease,
    transform 0.2s ease;
}

button[data-quick-view]:hover {
  background-color: #0056b3;
  transform: translateY(-2px);
}

button[data-quick-view]:focus {
  outline: none;
  box-shadow: 0 0 5px rgba(0, 123, 255, 0.5);
}

button[data-quick-view]:disabled {
  background-color: #c6c6c6;
  color: #999999;
  cursor: not-allowed;
}

button[data-close] {
  background-color: #dc3545;
  color: white;
  font-size: 16px;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition:
    background-color 0.3s ease,
    transform 0.2s ease;
}

button[data-close]:hover {
  background-color: #c82333;
  transform: translateY(-2px);
}

button[data-close]:focus {
  outline: none;
  box-shadow: 0 0 5px rgba(220, 53, 69, 0.5);
}

button[data-close]:disabled {
  background-color: #e2e6ea;
  color: #6c757d;
  cursor: not-allowed;
}
</style>
