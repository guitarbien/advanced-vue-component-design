<script>
export default {
  name: 'RenderlessTagInput',
  model: {
    prop: 'tags',
    event: 'update',
  },
  props: ['tags'],
  methods: {
    removeTag(tag) {
      this.$emit('update', this.tags.filter(t => t !== tag));
    },
  },
  render() {
    return this.$scopedSlots.default({
      tags: this.tags,
      removeTag: this.removeTag,
      inputProps: {
        value: this.input,
      },
      inputEvents: {
        input: (e) => this.input = e.target.value,
        keydown: (e) => {
          if (e.key === 'Backspace') {
            this.handleBackspace();
          }
          if (e.key === 'Enter') {
            e.preventDefault();
            this.addTag();
          }
        },
      },
    });
  },
};
</script>
