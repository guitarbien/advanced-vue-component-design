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
      on: {
        click: () => console.log('Clicked!'),
      },
    }, 'Hello World!');
  },
};
</script>
