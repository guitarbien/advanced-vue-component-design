<script>
export default {
  name: 'NewContactList',
  props: ['url'],
  data() {
    return {
      json: null,
      loading: true,
    };
  },
  created() {
    fetch(this.url)
      .then(response => response.json())
      .then((json) => {
        setTimeout(() => {
          this.json = json;
          this.loading = false;
        }, 2000);
      });
  },
  render() {
    return this.$scopedSlots.default({
      json: this.json,
      loading: this.loading,
    });
  },
};

</script>
