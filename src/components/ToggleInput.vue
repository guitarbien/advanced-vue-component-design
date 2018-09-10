<template>
<span class="toggle flex-no-shrink" role="checkbox" tabindex="0"
      :aria-checked="value"
      @click="toggle"
      @keydown.space.prevent="toggle"
></span>
</template>

<script>
export default {
  props: ['value'],
  methods: {
    toggle() {
      this.value = !this.value;
    },
  },
};
</script>
