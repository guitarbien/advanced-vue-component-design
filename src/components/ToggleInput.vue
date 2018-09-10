<template>
<span class="toggle flex-no-shrink" role="checkbox" tabindex="0"
      :aria-checked="toggled"
      @click="toggle"
      @keydown.space.prevent="toggle"
></span>
</template>

<script>
export default {
  model: {
    prop: 'toggled',
    event: 'toggle',
  },
  props: ['toggled'],
  methods: {
    toggle() {
      this.$emit('toggle', !this.toggled);
    },
  },
};
</script>
