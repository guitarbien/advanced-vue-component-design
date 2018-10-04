<script>
import ToggleInput from './ToggleInput.vue';

export default {
  name: 'HelloWorld',
  props: [],
  render(createElement) {
    // return createElement(element, attribute, child);
    return createElement(ToggleInput, {
      props: {
        toggled: true,
      },
    });
  },
};
</script>
