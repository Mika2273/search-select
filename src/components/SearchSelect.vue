<template>
  <div>
    <input
      class="search-filter-input"
      type="text"
      v-model="searchQuery"
      @click="showOptions = true"
      @input="filterOptions"
      @blur="handleBlur"
      @keydown.esc="showOptions = false"
      @keydown.up="highlightPrev"
      @keydown.down="highlightNext"
      @keydown.enter.prevent="selectHighlighted"
      autocomplete="off"
    />
    <input type="hidden" v-model="inputValue" :name="name" />
    <div class="dropdown-list-wrapper" v-show="showOptions">
      <span
        class="dropdown-list"
        v-for="(option, index) in filteredOptions"
        :key="index"
        @click="selectOption(option.name, option.value)"
        :style="{ backgroundColor: getColor(index) }"
      >
        {{ option.name }}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SearchSelect',
  props: {
    name: String,
    options: Array,
  },
  data() {
    return {
      filteredOptions: [],
      searchQuery: '',
      inputValue: null,
      showOptions: false,
      highlightedIndex: 0,
    };
  },
  mounted() {
    this.filteredOptions = this.options;
  },
  methods: {
    filterOptions() {
      this.showOptions = true;
      this.filteredOptions = this.options;
      if (this.searchQuery.length === 0) {
        return;
      }

      this.filteredOptions = this.filteredOptions.filter((option) => {
        const searchLength = this.searchQuery.length;
        return (
          option.name.slice(0, searchLength).toLowerCase() ===
          this.searchQuery.toLowerCase()
        );
      });
      this.highlightedIndex = 0;
    },
    selectOption(name, value) {
      this.searchQuery = name;
      this.inputValue = value;
      this.showOptions = false;
    },
    handleBlur() {
      for (let i = 0; i < this.options.length; i++) {
        if (
          this.options[i].name === this.searchQuery ||
          this.searchQuery === ''
        ) {
          return;
        }
      }

      if (this.filteredOptions.length === 0) {
        this.searchQuery = '';
        this.inputValue = null;
        this.showOptions = false;
        this.filteredOptions = this.options;
      }
      return;
    },
    getColor(index) {
      return index === this.highlightedIndex ? 'lightblue' : '';
    },
    highlightPrev() {
      if (this.highlightedIndex === 0) {
        return;
      }
      this.highlightedIndex -= 1;
      return;
    },
    highlightNext() {
      if (this.highlightedIndex === this.filteredOptions.length - 1) {
        return;
      }
      this.highlightedIndex += 1;
      return;
    },
    selectHighlighted() {
      if (Object.keys(this.filteredOptions).length !== 0) {
        this.selectOption(
          this.filteredOptions[this.highlightedIndex].name,
          this.filteredOptions[this.highlightedIndex].value,
        );
      }
    },
  },
};
</script>

<style scoped>
.search-filter-input {
  width: 200px;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.dropdown-list:hover {
  background-color: #efbbbb;
  cursor: pointer;
}

.dropdown-list-wrapper {
  display: flex;
  flex-direction: column;
  width: 200px;
  background-color: #f9f9fa;
  color: #6d7790;
  border: #0a47ff;
  padding: 5px;
  border-radius: 5px;
}
</style>
