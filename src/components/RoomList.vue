<template>
  <div class="row">
    <Room v-for="room in rooms" :key="room.id" :room="room"></Room>
    <AddStateButton/>
  </div>
</template>

<script>
import AddStateButton from '@/components/Add-state-button';
import Room           from '@/components/Room';
import axios          from "axios";

export default {
  name: 'RoomList', components: { AddStateButton, Room }, data() {
    return {
      rooms: [],
    }
  },
  created()
  {
    axios.get('http://localhost:3000/rooms').then(response => {
      this.rooms = response.data;
    });
  }
}
</script>

<style scoped>

</style>
