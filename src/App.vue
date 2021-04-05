<template>
  <div id="app">
    <div class="outerContainer">
      <div class="gridContainerSelected">
        <div
          class="selectedCurrency"
          v-for="selectedCurrency in selectedCurrencies"
          :key="selectedCurrency.id"
        >
          <button
            aria-label="Close"
            class="closeButton"
            v-on:click="select(selectedCurrency.id)"
          >
            <span aria-hidden="true">×</span>
          </button>
          {{ selectedCurrency.name }}
        </div>
      </div>
      <div class="gridContainer">
        <button
          class="button"
          v-bind:class="{ selected: currency.isSelected }"
          v-for="currency in currencies"
          :key="currency.id"
          v-on:click="select(currency.id)"
        >
          <div class="fakeCheckbox"></div>
          <cross />
          {{ currency.name }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import "./app.css";
import cross from "./components/cross.vue";

export default {
  name: "App",
  components: { cross },
  data() {
    return {
      currencies: [
        { id: 1, name: "EUR", isSelected: false, selectedAt: null },
        { id: 2, name: "PLN", isSelected: false, selectedAt: null },
        { id: 3, name: "GEL", isSelected: false, selectedAt: null },
        { id: 4, name: "DKK", isSelected: false, selectedAt: null },
        { id: 5, name: "CZK", isSelected: false, selectedAt: null },
        { id: 6, name: "GBP", isSelected: false, selectedAt: null },
        { id: 7, name: "SEK", isSelected: false, selectedAt: null },
        { id: 8, name: "USD", isSelected: false, selectedAt: null },
        { id: 9, name: "RUB", isSelected: false, selectedAt: null },
      ],
    };
  },
  methods: {
    select(id) {
      this.currencies.map((currency) => {
        if (currency.id === id) {
          currency.isSelected = !currency.isSelected;
          currency.selectedAt = new Date();
        }
        return currency;
      });
    },
  },
  computed: {
    selectedCurrencies: function() {
      const selected = this.currencies
        .filter((item) => item.isSelected === true)
        .sort((a, b) => a.selectedAt.getTime() - b.selectedAt.getTime());

      return selected;
    },
  },
};
</script>
