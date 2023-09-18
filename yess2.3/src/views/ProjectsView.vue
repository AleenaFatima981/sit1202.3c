<script setup>
// 3. Reactivity Fundamentals [ref(), <script setup>]
import { ref, computed, watch } from 'vue';

const message = ref('Welcome to SIT120!');

// 9. Watchers
watch(message, (newValue, oldValue) => {
  console.log(`Message changed from ${oldValue} to ${newValue}`);
});

// 2. Methods
const handleCustomEvent = (payload) => {
  console.log(`Custom event received with payload: ${payload}`);
};

const isChecked = ref(false);
const selectedOption = ref('Vue Basics');
const selectedItem = ref('item1');
const textAreaValue = ref('');
const isActive = ref(true);
const textColor = ref('blue');
const textSize = ref(18);
const objectData = ref({ topic1: 'Reactivity', topic2: 'Components' });
const range = (start, end) => Array.from({ length: end - start + 1 }, (_, i) => start + i);
const items = ref(['Introduction', 'Directives', 'Lifecycle', 'Vuex', 'Vue Router']);
const shouldShowItem = (item) => item.length % 2 === 0;
const componentsList = ref(['HeaderComponent', 'FooterComponent', 'SidebarComponent']);

// 7. Event Handling: Listening to Events [v-on:click]
// 7b. Method Handlers
const handleClick = () => {
  console.log('Button clicked!');
};

// 11. Router
import { RouterView } from "vue-router";
</script>

<template>
  <div>
    <div>This is the SIT120!</div>
    <!-- 1a. Text Interpolation -->
    <h1>{{ $route.params.id }}</h1>
    <!-- 11. Router -->
    <RouterView />
  </div>

  <div>
    <!-- 7. Event Handling: Listening to Events [v-on:click] -->
    <!-- 7a. Inline Handlers -->
    <button type="button" class="btn btn-link" v-on:click="handleClick">Explore Vue!</button>

    <!-- 8. Form Input Bindings -->
    <!-- 8a. v-model with <input type="text">, <input type="checkbox">, <input type="radio">, <select> and <textarea> -->
    <!-- 8b. v-model modifiers [.lazy , .number, .trim] -->
    <input type="text" v-model.lazy.number.trim="message" placeholder="Type your thoughts on Vue" />
    <input type="checkbox" v-model="isChecked" /> Enjoying Vue?
    <input type="radio" v-model="selectedOption" value="Vue Basics" /> Vue Basics
    <input type="radio" v-model="selectedOption" value="Advanced Vue" /> Advanced Vue
    <select v-model="selectedItem">
      <option value="item1">Just starting out</option>
      <option value="item2">Getting the hang of it</option>
      <option value="item3">Vue expert in the making</option>
    </select>
    <textarea v-model="textAreaValue" placeholder="Share your Vue experiences"></textarea>

    <!-- 5. Class and Style Bindings -->
    <!-- 5a. Binding HTML class [v-bind:class] -->
    <div :class="{ active: isActive }">Vue's class binding in action!</div>
    <!-- 5b. Binding Inline Styles [v-bind:style] -->
    <div :style="{ color: red, fontSize: textSize + 'px' }">
      Vue's style binding in action!
    </div>

    <!-- 6. List Rendering -->
    <!-- 6a. v-for with an Object -->
    <ul>
      <li v-for="(value, key) in objectData" :key="key">
        {{ key }}: {{ value }}
      </li>
    </ul>
    <!-- 6b. v-for with a Range -->
    <ul>
      <li v-for="number in range(1, 5)" :key="number">{{ number }}</li>
    </ul>
    <!-- 6c. v-for on <template> -->
    <!-- 6d. v-for with v-if -->
    <template v-for="(item, index) in items">
      <div v-if="shouldShowItem(item)">{{ item }}</div>
      <div v-else>Hidden Topic: {{ item }}</div>
    </template>
    <!-- 6e. v-for with a Component -->
    <div v-for="(component, index) in componentsList" :key="index">
      <!-- 10. Components -->
      <!-- 10a. Props -->
      <ComponentItem :name="component" @customEvent="handleCustomEvent" />
    </div>
  </div>
</template>

<style scoped>
.active {
  background-color: rgb(233, 233, 164);
}

.blue {
  color: rgb(155, 155, 190);
}
</style>
