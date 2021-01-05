<template>
  <div>
    <div v-b-toggle.sidebar-backdrop v-b-tooltip.hover class="h1 mb-2 pointer" title="Ouvrir le fil de discussion">
      <b-icon-chat-text></b-icon-chat-text>
    </div>

    <b-sidebar id="sidebar-backdrop" :backdrop-variant="variant" backdrop right shadow title="Fil de discussion">
      <div class="px-3 py-2">
        
      </div>
    </b-sidebar>
  </div>
</template>

<script>
export default {
  name: 'Chat', data()
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
    };
  },
};
</script>

<style scoped>

</style>
