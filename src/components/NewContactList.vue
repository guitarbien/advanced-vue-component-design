<template>
  <div>
    <div v-for="contact in contacts" :key="contact.id" class="flex items-center spaced-y-6">
      <img :src="contact.picture.medium" class="h-12 w-12 rounded-full block mr-2" alt="">
      <div>
        <div class="font-bold">
          {{ contact.name.first }} {{ contact.name.last }}
        </div>
        <div class="text-grey-dark">
          {{ contact.email }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NewContactList',
  props: ['contacts'],
};
</script>

<style scoped>

</style>
