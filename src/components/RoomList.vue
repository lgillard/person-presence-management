<template>
  <div class="row">
    <Room v-for="room in rooms" :key="room.name" :room="room"></Room>
    <div class="col-3">
      <div class="m-2 border-dark border-1" style="height: 50vh; text-align: center">
        <h2>+ Crée un état</h2>
      </div>
    </div>
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
  h2 {
    top: 50%;
    line-height: 50vh;
  }
</style>
