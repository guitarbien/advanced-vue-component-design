<script>
export default {
  name: 'HelloWorld',
  render(createElement) {
    // return createElement(element, attribute, child);
    return createElement('span', {
      attrs: {
        class: 'text-xl text-blue font-bold'
      }
    }, 'Hello World!');
  },
};
</script>
