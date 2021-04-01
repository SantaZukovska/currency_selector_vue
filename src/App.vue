<template>
  <div id="app">
    <div class="outerContainer">
      <div class="gridContainerSelected"></div>

      <div
        class="gridContainer"
      >
        <button class="button" v-for="currency in currencies"
        :key="currency.name">{{currency.name}}</button>
      </div>
    </div>
  </div>
</template>

<script>
import "./app.css";

export default {
  name: "App",
  components: {},
  data() {
    return {
      currencies: [
        { id: 1, name: "EUR", isSelected: false },
        { id: 2, name: "PLN", isSelected: false },
        { id: 3, name: "GEL", isSelected: false },
        { id: 4, name: "DKK", isSelected: false },
        { id: 5, name: "CZK", isSelected: false },
        { id: 6, name: "GBP", isSelected: false },
        { id: 7, name: "SEK", isSelected: false },
        { id: 8, name: "USD", isSelected: false },
        { id: 9, name: "RUB", isSelected: false },
      ],
    };
  },
};
</script>


