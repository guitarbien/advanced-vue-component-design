<script>
import ToggleInput from './ToggleInput.vue';

export default {
  name: 'HelloWorld',
  props: [],
  data() {
    return {
      enabled: true,
    };
  },
  render(createElement) {
    // return createElement(element, attribute, child);
    return createElement(ToggleInput, {
      props: {
        toggled: this.enabled,
      },
    });
  },
};
</script>
