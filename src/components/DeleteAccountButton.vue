<template>
  <button type="button"
          @click="confirmDeleteModalOpen = true"
  >
    <slot></slot>
    <confirm-delete-modal :show="confirmDeleteModalOpen"
                          @close="confirmDeleteModalOpen = false"
                          :account-id="accountId"
    ></confirm-delete-modal>
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
