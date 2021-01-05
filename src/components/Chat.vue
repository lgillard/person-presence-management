<template>
  <div>
    <div v-b-toggle.sidebar-backdrop v-b-tooltip.hover class="h1 mb-2 pointer" title="Ouvrir le fil de discussion">
      <b-icon-chat-text></b-icon-chat-text>
    </div>

    <b-sidebar id="sidebar-backdrop" :backdrop-variant="variant" backdrop right shadow title="Fil de discussion">
      <div class="px-3 py-2">
        <MessagesBox/>
        <label class="d-block" for="message">Message :</label>
        <input id="message" v-model="message" placeholder="Entrer votre message ici" type="text"/>
        <button v-b-tooltip.hover class="pointer" title="Envoyer" type="submit" @click="sendMessage">
          <b-icon-arrow-right></b-icon-arrow-right>
        </button>
      </div>
    </b-sidebar>
  </div>
</template>

<script>
import MessagesBox from '@/components/MessagesBox';

export default {
  name:       'Chat', components: { MessagesBox }, data()
  {
    return {
      variant:  'dark',
      variants: ['transparent',
                 'white',
                 'light',
                 'dark',
                 'primary',
                 'secondary',
                 'success',
                 'danger',
                 'warning',
                 'info'],
      message:  '',
    };
  }, methods: {
    sendMessage()
    {
      // TODO send message by using websocket
      console.log('message were sent : ' + this.message);
      this.message = '';
    },
  },
};
</script>

<style scoped>

</style>
