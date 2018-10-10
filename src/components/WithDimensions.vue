<script>
import elementResizeDetectorMaker from 'element-resize-detector';

const erd = elementResizeDetectorMaker({ strategy: 'scroll' });

export default {
  name: 'WithDimensions',
  data() {
    return {
      width: null,
      height: null,
    };
  },
  mounted() {
    erd.listenTo(this.$el, (el) => {
      this.width = el.offsetWidth;
      this.height = el.offsetHeight;
    });
  },
  render() {
    return this.$scopedSlots.default({
      width: this.width,
      height: this.height,
    });
  },
};
</script>
