<template>
  <div v-b-tooltip.hover class="h1 mb-2 pointer" title="Conversation" @click="chatClicked">
    <b-icon-chat-text></b-icon-chat-text>
  </div>
</template>

<script>
export default {
  name: 'Chat-icon', methods: {
    chatClicked()
    {
      this.$emit('chatIconClicked');
    },
  },
};
</script>

<style scoped>

</style>
