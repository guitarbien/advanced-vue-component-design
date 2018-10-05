<script>
/** @type {Array} */
import contacts from '../../public/contact.json';
import ToggleInput from './ToggleInput.vue';

export default {
  name: 'HelloWorld',
  props: [],
  data() {
    return {
      contacts,
      enabled: true,
    };
  },
  render(createElement) {
    console.log(
      this.$scopedSlots.default({
        subject: 'world',
      }));

    return createElement('div', {}, [
      createElement(ToggleInput, {
        props: {
          toggled: this.enabled,
        },
        on: {
          toggle: (newValue) => {
            this.enabled = newValue;
          },
        },
      }),
      createElement('h1', {}, 'Your Contacts'),
      createElement('ul', {}, this.contacts.map(contact => createElement('li', {}, `${contact.name.first} ${contact.name.last}`))),
      createElement('span', {
        attrs: {
          class: 'text-xl text-blue font-bold',
        },
      }, [
        this.$scopedSlots.default({
          subject: 'world',
        }),
      ]),
    ]);
  },
};
</script>
