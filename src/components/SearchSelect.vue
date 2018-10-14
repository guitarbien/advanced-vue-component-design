<template>
  <div class="search-select" :class="{ 'is-active' : isOpen}">
    <button type="button" @click="open" class="search-select-input">
      <span v-if="value !== null">{{ value }}</span>
      <span v-else class="search-select-placeholder">Select a band...</span>
    </button>
    <div v-show="isOpen" class="search-select-dropdown">
      <input class="search-select-search" v-model="search">
      <ul class="search-select-options">
        <li class="search-select-option"
            v-for="option in filteredOptions"
            :key="option"
            @click="select(option)"
        >{{ option }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SearchSelect',
  data() {
    return {
      value: 'Destruction',
      isOpen: false,
      search: '',
      options: [
        'Anthrax',
        'Dark Angel',
        'Destruction',
        'Exodus',
        'Flotsam and Jetsam',
        'Kreator',
        'Megadeth',
        'Metallica',
        'Overkill',
        'Sepultura',
        'Slayer',
        'Testament',
      ],
    };
  },
  computed: {
    filteredOptions() {
      return this.options.filter(option => option.toLowerCase().startsWith(this.search.toLowerCase()));
    },
  },
  methods: {
    open() {
      this.isOpen = true;
    },
    close() {
      this.isOpen = false;
    },
    select(option) {
      this.value = option;
      this.close();
    },
  },
};
</script>
