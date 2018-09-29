<template>
  <portal to="modals" v-if="show">
    <div class="modal-backdrop">
      <div class="modal">
        <slot></slot>
      </div>
    </div>
  </portal>
</template>

<script>
export default {
  name: 'ModalDialog',
  props: ['show'],
  watch: {
    show: {
      immediate: true,
      handler: (show) => {
        if (show) {
          document.body.style.setProperty('overflow', 'hidden');
        } else {
          document.body.style.removeProperty('overflow');
        }
      },
    },
  },
  methods: {
    cancel() {
      this.$emit('close');
    },
  },
  created() {
    const escapeHandler = (e) => {
      if (e.key === 'Escape' && this.show) {
        this.cancel();
      }
    };
    document.addEventListener('keydown', escapeHandler);
    this.$once('hook:destroyed', () => {
      document.removeEventListener('keydown', escapeHandler);
    });
  },
};
</script>

<style scoped>

</style>
