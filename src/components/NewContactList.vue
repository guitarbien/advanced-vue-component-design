<script>
export default {
  name: 'NewContactList',
  data() {
    return {
      contacts: [],
    };
  },
  created() {
    fetch('contact.json')
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
