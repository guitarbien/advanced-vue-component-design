<script>
import { Sortable } from '@shopify/draggable';

export default {
  name: 'SortableList',
  mounted() {
    new Sortable(document.querySelectorAll('.contact-list'), {
      draggable: '.contact-list-item',
      handle: '.contact-list-handle',
      mirror: {
        constrainDimensions: true,
      },
    });
  },
  render() {
    return this.$slots.default[0];
  },
};
</script>
