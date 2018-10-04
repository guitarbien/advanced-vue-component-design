<script>
export default {
  name: 'HelloWorld',
  props: ['tag'],
  render(createElement) {
    // return createElement(element, attribute, child);
    return createElement(this.tag, {
      attrs: {
        class: 'btn btn-blue',
      },
    }, 'Hello World!');
  },
};
</script>
