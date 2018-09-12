<template>
  <button type="button" class="text-red-dark hover:underline"
          @click="confirmDeleteModalOpen = true"
  >
    Delete Account
    <portal to="modals">
      <confirm-delete-modal :show="confirmDeleteModalOpen"
                            @close="confirmDeleteModalOpen = false"
                            :account-id="accountId"
      ></confirm-delete-modal>
    </portal>
  </button>
</template>

<script>
import ConfirmDeleteModal from './ConfirmDeleteModal.vue';

export default {
  name: 'DeleteAccountButton',
  components: {
    ConfirmDeleteModal,
  },
  props: ['accountId'],
  data() {
    return {
      confirmDeleteModalOpen: false,
    };
  },
};
</script>

<style scoped>

</style>
