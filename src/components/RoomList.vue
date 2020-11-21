<template>
  <div class="row">
    <Room v-for="room in rooms" :key="room.id" :room="room"></Room>
    <AddStateButton @newStateCreated="() => {updateList}"/>
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
    this.updateList();
    setInterval(this.updateList, 10000);
  },
  methods: {
    updateList() {
      axios.get('http://localhost:3000/rooms').then(response => {
        this.rooms = response.data;
      });
    }
  }
}
</script>

<style scoped>

</style>
