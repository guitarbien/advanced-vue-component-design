<template>
  <div class="tag-input">
    <span v-for="tag in tags" :key="tag" class="tag-input-tag">
      <span>{{ tag }}</span>
      <button type="button" class="tag-input-remove"
              @click="removeTag(tag)"
      >&times;</button>
    </span>
    <input class="tag-input-text" placeholder="Add tag..."
           v-model="input"
           @keydown.backspace="handleBackspace"
           @keydown.enter.prevent="addTag"
    >
  </div>
</template>

<script>
export default {
  name: 'TagInput',
  model: {
    prop: 'tags',
    event: 'update',
  },
  props: ['tags'],
  data() {
    return {
      input: '',
    };
  },
  computed: {
    newTag() {
      return this.input.trim();
    },
  },
  methods: {
    removeTag(tag) {
      this.$emit('update', this.tags.filter(t => t !== tag));
    },
    addTag() {
      if (this.newTag.length === 0 || this.tags.includes(this.newTag)) {
        return;
      }
      this.$emit('update', [...this.tags, this.newTag]);
      this.clearInput();
    },
    clearInput() {
      this.input = '';
    },
    handleBackspace() {
      if (this.newTag.length === 0) {
        this.$emit('update', this.tags.slice(0, -1));
      }
    },
  },
};
</script>
