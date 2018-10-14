<template>
  <div class="search-select is-active">
    <div class="search-select-input">
      <span>Dark Angel</span>
      <!--<span class="search-select-placeholder">Select a band...</span>-->
      <span v-if="value !== null">{{ value }}</span>
      <span v-else class="search-select-placeholder">Select a band...</span>
    </div>
    <div class="search-select-dropdown">
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
};
</script>
