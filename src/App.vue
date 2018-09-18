<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <!-- 01 -->
      <user-settings-form :account-id="accountId"></user-settings-form>

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

      <!-- 06 -->
      <portal-target name="modals"></portal-target>
      <!-- 07 -->
      <!--<portal-target name="tooltips"></portal-target>-->
      <!--<portal-target name="dropdowns"></portal-target>-->

      <!-- 03 -->
      <div class="card justify-center">
        <p class="mb-6">It was the best of times, it was the worst of times, it was the age of wisdom, it was the age of foolishness, it was the epoch of belief, it was the epoch of incredulity, it was the season of Light, it was the season of Darkness, it was the spring of hope, it was the winter of despair, we had everything before us, we had nothing before us, we were all going direct to Heaven, we were all going direct the other way--in short, the period was so far like the present period, that some of its noisiest authorities insisted on its being received, for good or for evil, in the superlative degree of comparison only.</p>
        <button @click="modalOpen = true" type="button" class="btn btn-blue">Open Modal</button>
        <p class="mb-6">France, less favoured on the whole as to matters spiritual than her sister of the shield and trident, rolled with exceeding smoothness down hill, making paper money and spending it. Under the guidance of her Christian pastors, she entertained herself, besides, with such humane achievements as sentencing a youth to have his hands cut off, his tongue torn out with pincers, and his body burned alive, because he had not kneeled down in the rain to do honour to a dirty procession of monks which passed within his view, at a distance of some fifty or sixty yards. It is likely enough that, rooted in the woods of France and Norway, there were growing trees, when that sufferer was put to death, already marked by the Woodman, Fate, to come down and be sawn into boards, to make a certain movable framework with a sack and a knife in it, terrible in history. It is likely enough that in the rough outhouses of some tillers of the heavy lands adjacent to Paris, there were sheltered from the weather that very day, rude carts, bespattered with rustic mire, snuffed about by pigs, and roosted in by poultry, which the Farmer, Death, had already set apart to be his tumbrils of the Revolution. But that Woodman and that Farmer, though they work unceasingly, work silently, and no one heard them as they went about with muffled tread: the rather, forasmuch as to entertain any suspicion that they were awake, was to be atheistical and traitorous.</p>
      </div>

      <portal to="modals" v-if="modalOpen">
        <announcement-modal :show="modalOpen"
                            :preventBackgroundScrolling="false"
                            @close="modalOpen = false"
        ></announcement-modal>
      </portal>

      <!-- 08 -->
      <div class="text-center p-8 my-8">
        <button type="button" class="btn btn-blue">Click me</button>
        <primary-button text="Download"></primary-button>
      </div>

    </div>
  </div>
</template>

<script>
import UserSettingsForm from './components/UserSettingsForm.vue';
import DatePicker from './components/DatePicker.vue';
import AnnouncementModal from './components/AnnouncementModal.vue';
import PrimaryButton from './components/PrimaryButton.vue';

export default {
  components: {
    UserSettingsForm,
    DatePicker,
    AnnouncementModal,
    PrimaryButton,
  },
  data() {
    return {
      date: 'Apr 12 2018',
      // set to true the modal will open by default, and the scrollbar should be disabled
      modalOpen: true,
      accountId: 7,
    };
  },
};
</script>

<style src="./assets/css/pikaday.css"></style>
<style src="./assets/css/app.css"></style>
