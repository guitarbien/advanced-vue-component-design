<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <user-settings-form></user-settings-form>

      <div class="card">
        <label class="block">
          <span class="form-label mb-2">Select a date</span>
          <input :value="date" class="form-input" type="text" id="datePicker" placeholder="YYYY-MM-DD">
        </label>
      </div>

    </div>
  </div>
</template>

<script>
import Pikaday from 'pikaday';
import UserSettingsForm from './components/UserSettingsForm.vue';

export default {
  components: {
    UserSettingsForm,
  },
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

<style src="./assets/css/pikaday.css"></style>
<style src="./assets/css/app.css"></style>
