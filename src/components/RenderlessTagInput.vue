<script>
export default {
  name: 'RenderlessTagInput',
  model: {
    prop: 'tags',
    event: 'update',
  },
  props: ['tags'],
  render() {
    return this.$scopedSlots.default({

    });
  },
};
</script>
