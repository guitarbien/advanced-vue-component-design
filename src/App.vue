<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <user-settings-form></user-settings-form>

      <div class="card">
        <label class="block">
          <span class="form-label mb-2">Select a date</span>
          <date-picker></date-picker>
        </label>
      </div>

    </div>
  </div>
</template>

<script>
import UserSettingsForm from './components/UserSettingsForm.vue';
import DatePicker from './components/DatePicker.vue';

export default {
  components: {
    UserSettingsForm,
    DatePicker,
  },
  data() {
    return {
      date: '2018-04-12',
    };
  },
};
</script>

<style src="./assets/css/pikaday.css"></style>
<style src="./assets/css/app.css"></style>
