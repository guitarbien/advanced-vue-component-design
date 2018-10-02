<template>
  <button type="button" class="btn btn-blue">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'PrimaryButton',
  props: ['text'],
};
</script>

<style scoped>

</style>
