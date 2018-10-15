<template>
  <div class="search-select" :class="{ 'is-active' : isOpen}">
    <button ref="button" type="button" @click="open" class="search-select-input">
      <span v-if="value !== null">{{ value }}</span>
      <span v-else class="search-select-placeholder">Select a band...</span>
    </button>
    <div v-show="isOpen" class="search-select-dropdown">
      <input class="search-select-search"
             v-model="search"
             ref="search"
             @keydown.esc="close"
             @keydown.down="highlightNext"
             @keydown.up="highlightPrev"
             @keydown.enter.prevent="selectHighlighted"
      >
      <ul ref="options" v-show="filteredOptions.length > 0" class="search-select-options">
        <li class="search-select-option" :class="{ 'is-active': index === highlightedIndex }"
            v-for="(option, index) in filteredOptions"
            :key="option"
            @click="select(option)"
        >{{ option }}</li>
      </ul>
      <div v-show="filteredOptions.length <= 0" class="search-select-empty">
        No results found for "{{ search }}"
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SearchSelect',
  props: ['value', 'options', 'filterFunction'],
  data() {
    return {
      isOpen: false,
      search: '',
      highlightedIndex: 0,
    };
  },
  computed: {
    filteredOptions() {
      return this.filterFunction(this.search, this.options);
    },
  },
  methods: {
    open() {
      if (this.isOpen) {
        return;
      }

      this.isOpen = true;
      this.$nextTick(() => {
        this.$refs.search.focus();
        this.scrollToHighlighted();
      });
    },
    close() {
      this.isOpen = false;
      this.$refs.button.focus();
    },
    select(option) {
      this.$emit('input', option);
      this.search = '';
      this.highlightedIndex = 0;
      this.close();
    },
    selectHighlighted() {
      this.select(this.filteredOptions[this.highlightedIndex]);
    },
    scrollToHighlighted() {
      this.$refs.options.children[this.highlightedIndex].scrollIntoView({ block: 'nearest' });
    },
    highlight(index) {
      this.highlightedIndex = index;

      if (this.highlightedIndex < 0) {
        this.highlightedIndex = this.filteredOptions.length - 1;
      }

      if (this.highlightedIndex > this.filteredOptions.length - 1) {
        this.highlightedIndex = 0;
      }

      this.scrollToHighlighted();
    },
    highlightNext() {
      this.highlight(this.highlightedIndex + 1);
    },
    highlightPrev() {
      this.highlight(this.highlightedIndex - 1);
    },
  },
};
</script>
