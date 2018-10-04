<template>
  <primary-button>
    Hello World 02!
  </primary-button>
</template>
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
