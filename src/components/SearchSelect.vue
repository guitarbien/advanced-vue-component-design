<template>
  <div class="search-select is-active">
    <button type="button" @click="open" class="search-select-input">
      <span v-if="value !== null">{{ value }}</span>
      <span v-else class="search-select-placeholder">Select a band...</span>
    </button>
    <div v-show="isOpen" class="search-select-dropdown">
      <input class="search-select-search">
      <ul class="search-select-options">
        <li class="search-select-option"
            v-for="option in options"
            :key="option"
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
  methods: {
    open() {
      this.isOpen = true;
    },
  },
};
</script>
