<template>
  <ul>
    <li v-for="(contact, key) in contacts" :key="key">
      {{ contact.name.first}} {{ contact.name.last}}
    </li>
  </ul>
</template>

<script>
import contacts from '../../public/contact.json';

export default {
  name: 'HelloList',
  data() {
    return {
      contacts,
    };
  },
};
</script>
