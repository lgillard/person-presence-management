<template>
  <div class="messages-box border-dark">
    <message v-for="(message, index) in messageList" :key="index" :message="message"/>
    <div v-if="messageList.length <= 0">Aucun message</div>
  </div>
</template>

<script>
import Message from '@/components/Message';

export default {
  name: 'MessagesBox', components: { Message }, props: {
    messageList: {
      type: Array, default: () => [],
    },
  },
};
</script>

<style scoped>
.messages-box
{
  border:        thin solid;
  border-radius: 5px;
  height:        70vh;
  margin-bottom: 3vh;
  padding:       1vh;
}
</style>
