<script>
/** @type {Array} */
import contacts from '../../public/contact.json';

export default {
  name: 'HelloList',
  data() {
    return {
      contacts,
    };
  },
  render(createElement) {
    return createElement('ul', {}, this.contacts.map(contact => createElement('li', {}, `${contact.name.first} ${contact.name.last}`)));
  },
};
</script>
