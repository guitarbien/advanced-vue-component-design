<template>
  <renderless-tag-input :tags="tags"
                        @update="(newTags) => $emit('update', newTags)"
                        :remove-on-backspace="false"
  >
    <div class="stacked-tag-input" slot-scope="{ tags, addTag, removeButtonEvents, inputProps, inputEvents }">
      <div class="stacked-tag-input-form">
        <input class="form-input" placeholder="Add tag..."
               v-bind="inputProps"
               v-on="inputEvents"
        >
        <button class="btn btn-indigo"
                @click="addTag"
        >Add Tag</button>
      </div>
      <ul class="stacked-tag-list">
        <li v-for="tag in tags" :key="tag">
          {{ tag }}
          <button type="button" class="stacked-tag-link" v-on="removeButtonEvents(tag)">Remove</button>
        </li>
      </ul>
    </div>
  </renderless-tag-input>
</template>

<script>
import RenderlessTagInput from './RenderlessTagInput.vue';

export default {
  name: 'StackedTagInput',
  components: {
    RenderlessTagInput,
  },
  model: {
    prop: 'tags',
    event: 'update',
  },
  props: {
    tags: { required: true },
  },
};
</script>

<style scoped>

</style>
