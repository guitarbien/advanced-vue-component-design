<template>
  <form class="card" @submit.prevent="submit">
    <h1 class="text-2xl font-bold mb-6">Your Settings</h1>
    <label class="block mb-6">
      <span class="form-label mb-2">Email Address</span>
      <input v-model="email" class="form-input" placeholder="you@example.com">
    </label>
    <div class="mb-8">
      <span class="form-label mb-2">Newsletter</span>
      <div class="flex justify-between items-center">
        <p class="mr-4">Send you occasional news and updates.</p>
        <toggle-input v-model="receiveNewsletter"></toggle-input>
      </div>
    </div>
    <div class="flex justify-between" style="opacity: .5">
      <button type="button" class="text-red-dark hover:underline"
              @click="confirmDeleteModalOpen = true"
      >Delete Account</button>

      <portal to="modals">
        <confirm-delete-modal :show="confirmDeleteModalOpen"
                              @close="confirmDeleteModalOpen = false"
                              :account-id="accountId"
        ></confirm-delete-modal>
      </portal>

      <button type="submit" class="btn btn-blue">Update Settings</button>
    </div>
  </form>
</template>

<script>

import ToggleInput from './ToggleInput.vue';
import ConfirmDeleteModal from './ConfirmDeleteModal.vue';

export default {
  components: {
    ToggleInput,
    ConfirmDeleteModal,
  },
  props: ['accountId'],
  data() {
    return {
      email: 'jane@example.com',
      receiveNewsletter: false,
      confirmDeleteModalOpen: false,
    };
  },
  methods: {
    submit() {
      console.log('Submitting preferences...', {
        email: this.email,
        receiveNewsletter: this.receiveNewsletter,
      });
    },
  },
};
</script>
