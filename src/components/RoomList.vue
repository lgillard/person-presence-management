<template>
  <div class="row">
    <Room v-for="room in rooms" :key="room.name" :room="room"></Room>
  </div>
</template>

<script>
import Room  from '@/components/Room';
import axios from "axios";

export default {
  name: 'RoomList', components: { Room }, data() {
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
