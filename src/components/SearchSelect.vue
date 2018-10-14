<template>
  <div class="search-select is-active">
    <div class="search-select-input">
      <span>Dark Angel</span>
      <!--<span class="search-select-placeholder">Select a band...</span>-->
    </div>
    <div class="search-select-dropdown">
      <input class="search-select-search">
      <ul class="search-select-options">
        <li class="search-select-option">Anthrax</li>
        <li class="search-select-option is-active">Dark Angel</li>
        <li class="search-select-option">Destruction</li>
        <li class="search-select-option">Exodus</li>
        <li class="search-select-option">Flotsam and Jetsam</li>
        <li class="search-select-option">Kreator</li>
        <li class="search-select-option">Megadeth</li>
        <li class="search-select-option">Metallica</li>
        <li class="search-select-option">Overkill</li>
        <li class="search-select-option">Sepultura</li>
        <li class="search-select-option">Slayer</li>
        <li class="search-select-option">Testament</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SearchSelect',
  },
};
</script>
