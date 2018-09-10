<template>
  <input :value="value"
         ref="input" class="form-input" type="text" id="datePicker" placeholder="YYYY-MM-DD">
</template>

<script>
import Pikaday from 'pikaday';

export default {
  name: 'DatePicker',
  props: {
    value: { required: true },
    format: { default: 'YYYY-MM-DD' },
    options: { default: {} },
  },
  mounted() {
    const picker = new Pikaday({
      field: this.$refs.input,
      format: this.format,
      onSelect: () => {
        this.$emit('input', picker.toString());
      },
      ...this.options,
    });
  },
};
</script>

<style scoped>

</style>
