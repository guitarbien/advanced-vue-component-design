<template>
  <modal-dialog :show="show" @close="cancel">
    <h1 class="text-center text-2xl font-bold mb-4">
      Are you sure?
    </h1>
    <p class="text-center text-grey-darker mb-6">
      Deleting your account cannot be undone.
    </p>
    <div class="text-center">
      <button @click="cancel" type="button" class="btn btn-grey mr-4">
        Cancel
      </button>
      <button @click="confirmDelete" type="button" class="btn btn-red">
        Delete it
      </button>
    </div>
  </modal-dialog>
</template>

<script>
import ModalDialog from './ModalDialog.vue';

export default {
  name: 'ConfirmDeleteModal',
  components: {
    ModalDialog,
  },
  props: ['show', 'accountId'],
  methods: {
    cancel() {
      this.$emit('close');
    },
    confirmDelete() {
      console.log(`Deleting account ${this.accountId}...`);
      this.$emit('close');
    },
  },
};
</script>

<style scoped>

</style>
