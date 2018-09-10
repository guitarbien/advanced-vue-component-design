<template>
  <input :value="value" class="form-input" type="text" id="datePicker" placeholder="YYYY-MM-DD">
</template>

<script>
import Pikaday from 'pikaday';

export default {
  name: 'DatePicker',
  props: ['value'],
  mounted() {
    const picker = new Pikaday({
      field: document.getElementById('datePicker'),
      format: 'YYYY-MM-DD',
      onSelect: () => {
        this.$emit('input', picker.toString());
      },
    });
  },
};
</script>

<style scoped>

</style>
