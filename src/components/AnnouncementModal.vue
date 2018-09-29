<template>
  <modal-dialog :show="show" @close="dismiss">
    <h1 class="text-center text-2xl font-bold mb-4">
      Exciting new features are here!
    </h1>
    <p class="text-center text-grey-darker mb-6">
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. At ut eligendi quod tempore totam
      explicabo sit consectetur architecto? Tempora, repellat est rem ut esse ab officia saepe
      ratione tempore. Obcaecati.
    </p>
    <div class="text-center">
      <button @click="dismiss" type="button" class="btn btn-blue">
        Dismiss
      </button>
    </div>
  </modal-dialog>
</template>

<script>
import ModalDialog from './ModalDialog.vue';

export default {
  components: {
    ModalDialog,
  },
  props: {
    show: { required: true },
    preventBackgroundScrolling: { default: true },
  },
  methods: {
    dismiss() {
      this.$emit('close');
    },
  },
};
</script>

<style scoped>

</style>
