<script>
export default {
  name: 'onClickOutside',
  props: ['do'],
  render() {
    return this.$slots.default[0];
  },
};
</script>
