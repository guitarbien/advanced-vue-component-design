<script>
import PrimaryButton from './PrimaryButton.vue';

export default {
  name: 'HelloWorld',
  components: {
    PrimaryButton,
  },
  props: ['tag'],
  render(createElement) {
    // return createElement(element, attribute, child);
    return createElement(PrimaryButton, {
      on: {
        click: () => console.log('Clicked!'),
      },
    }, 'Hello World 02!');
  },
};
</script>
