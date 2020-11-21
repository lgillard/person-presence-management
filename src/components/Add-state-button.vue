<template>
  <div class="col-3">
    <div class="m-2 pointer border-dark border-1 box" @click="createDefaultState">
      <h2 class="vertical-center">+ Crée un état</h2>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Add-state-button', methods: {
    createDefaultState()
    {
      const defaultState = { name: 'Nouvel état', color: '#9ba0a3' };
      axios.post('http://localhost:3000/rooms', defaultState).then(() =>
                                                                   {
                                                                     this.$emit('newStateCreated');
                                                                   });
    },
  },
};
</script>

<style scoped>
.vertical-center
{
  line-height: 50vh;
  top:         50%;
}
</style>
