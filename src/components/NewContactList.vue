<script>
export default {
  name: 'NewContactList',
  props: ['url'],
  data() {
    return {
      contacts: [],
    };
  },
  created() {
    fetch(this.url)
      .then(response => response.json())
      .then((contacts) => {
        this.contacts = contacts;
      });
  },
  render() {
    return this.$scopedSlots.default({
      contacts: this.contacts,
    });
  },
};

</script>
