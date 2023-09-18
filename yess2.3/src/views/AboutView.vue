<template>
  
  <div>
    <h1 style="color: red;">{{ $route.params.id }}</h1>
    <button v-on:click="handleClick">Click me!</button>
    <button type="button" class="btn btn-primary">Primary</button>
    <button type="button" class="btn btn-secondary">Secondary</button>
    <button type="button" class="btn btn-success">Success</button>
    <button type="button" class="btn btn-danger">Danger</button>
    <button type="button" class="btn btn-warning">Warning</button>
    <button type="button" class="btn btn-info">Info</button>
    <button type="button" class="btn btn-light">Light</button>
    <button type="button" class="btn btn-dark">Dark</button>

<button type="button" class="btn btn-link">Link</button>

    <input type="text" v-model.lazy.number.trim="message" />
    <input type="checkbox" v-model="isChecked" />
    <input type="radio" v-model="selectedOption" value="option1" />
    <input type="radio" v-model="selectedOption" value="option2" />
    <select v-model="selectedItem">
      <option value="item1">Item 1</option>
      <option value="item2">Item 2</option>
      <option value="item3">Item 3</option>
    </select>
    <textarea v-model="textAreaValue"></textarea>

    <div :class="{ active: isActive }">Binding HTML class</div>

    <div :style="{ color: textColor, fontSize: textSize + 'px' }">
      Binding Inline Styles
    </div>

    <ul>
      <li v-for="(value, key) in objectData" :key="key">
        {{ key }}: {{ value }}
      </li>
    </ul>

    <ul>
      <li v-for="number in range(1, 5)" :key="number">{{ number }}</li>
    </ul>

    <template v-for="(item, index) in items">
      <div v-if="shouldShowItem(item)">{{ item }}</div>
      <div v-else>Not showing item {{ item }}</div>
    </template>

    <div v-for="(item, index) in itemsWithComponents" :key="index">
      <MyComponent :item="item" />
    </div>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue';



const message = ref('Hello, world!');

watch(message, (newValue, oldValue) => {
  console.log(`Message changed from ${oldValue} to ${newValue}`);
});

const handleCustomEvent = (payload) => {
  console.log(`Custom event received with payload: ${payload}`);
};

const isChecked = ref(false);
const selectedOption = ref('option1');
const selectedItem = ref('item1');
const textAreaValue = ref('');
const isActive = ref(true);
const textColor = ref('red');
const textSize = ref(16);
const objectData = ref({ key1: 'value1', key2: 'value2' });
const range = (start, end) => Array.from({ length: end - start + 1 }, (_, i) => start + i);
const items = ref([1, 2, 3, 4, 5]);
const shouldShowItem = (item) => item % 2 === 0;
const itemsWithComponents = ref(['Component A', 'Component B', 'Component C']);

const handleClick = () => {
  console.log('Button clicked!');
};
</script>

<style scoped>
.active {
  background-color: yellow;
}

.red {
  color: red;
}
</style>
