<script>
import { Sortable } from '@shopify/draggable';

export default {
  name: 'SortableList',
  props: {
    itemClass: {
      default: 'sortable-list-item',
    },
    handleClass: {
      default: 'sortable-list-handle',
    },
  },
  provide() {
    return {
      sortableListItemClass: this.itemClass,
      sortableListHandleClass: this.handleClass,
    };
  },
  mounted() {
    new Sortable(this.$el, {
      draggable: `.${this.itemClass}`,
      handle: `.${this.handleClass}`,
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
