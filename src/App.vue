<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <!-- 01 -->
      <user-settings-form></user-settings-form>

      <!-- 02 -->
      <div class="card">
        <label class="block">
          <span class="form-label mb-2">Select a date</span>
          <date-picker v-model="date"
                       format="MMM D YYYY"
                       :options="{ firstDay: 1 }"
          ></date-picker>
        </label>
      </div>

      <!-- 03 -->
      <div class="card flex justify-center">
        <button @click="modalOpen = true" type="button" class="btn btn-blue">Open Modal</button>
      </div>
      <announcement-modal :show="modalOpen" @close="modalOpen = false"></announcement-modal>

    </div>
  </div>
</template>

<script>
import UserSettingsForm from './components/UserSettingsForm.vue';
import DatePicker from './components/DatePicker.vue';
import AnnouncementModal from './components/AnnouncementModal.vue';

export default {
  components: {
    UserSettingsForm,
    DatePicker,
    AnnouncementModal,
  },
  data() {
    return {
      date: 'Apr 12 2018',
      modalOpen: false,
    };
  },
};
</script>

<style src="./assets/css/pikaday.css"></style>
<style src="./assets/css/app.css"></style>
