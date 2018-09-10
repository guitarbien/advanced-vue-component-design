<template>
  <input :value="date" class="form-input" type="text" id="datePicker" placeholder="YYYY-MM-DD">
</template>

<script>
import Pikaday from 'pikaday';

export default {
  name: 'DatePicker',
  data() {
    return {
      date: '2018-04-12',
    };
  },
  mounted() {
    const picker = new Pikaday({
      field: document.getElementById('datePicker'),
      format: 'YYYY-MM-DD',
      onSelect: () => {
        this.date = picker.toString();
      },
    });
  },
};
</script>

<style scoped>

</style>
