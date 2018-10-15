<template>
  <on-click-outside :do="close">
    <div class="search-select" :class="{ 'is-active' : isOpen}">
      <button ref="button" type="button" @click="open" class="search-select-input">
        <span v-if="value !== null">{{ value }}</span>
        <span v-else class="search-select-placeholder">Select a band...</span>
      </button>
      <div ref="dropdown" v-show="isOpen" class="search-select-dropdown">
        <input class="search-select-search"
               v-model="search"
               ref="search"
               @keydown.esc="close"
               @keydown.down="highlightNext"
               @keydown.up="highlightPrev"
               @keydown.enter.prevent="selectHighlighted"
               @keydown.tab.prevent
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
  </on-click-outside>
</template>

<script>
import Popper from 'popper.js';
import OnClickOutside from './OnClickOutside.vue';

export default {
  name: 'SearchSelect',
  props: ['value', 'options', 'filterFunction'],
  components: {
    OnClickOutside,
  },
  data() {
    return {
      isOpen: false,
      search: '',
      highlightedIndex: 0,
    };
  },
  beforeDestroy() {
    this.popper.destroy();
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
        this.setupPopper();
        this.$refs.search.focus();
        this.scrollToHighlighted();
      });
    },
    setupPopper() {
      if (this.popper === undefined) {
        // new Popper(reference, element, options);
        this.popper = new Popper(this.$refs.button, this.$refs.dropdown, {
          placement: 'bottom',
        });
      } else {
        this.popper.scheduleUpdate();
      }
    },
    close() {
      if (!this.isOpen) {
        return;
      }

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
