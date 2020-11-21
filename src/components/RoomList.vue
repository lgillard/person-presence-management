<template>
  <div class="row">
    <Room v-for="room in rooms" :key="room.id" :room="room" :users="users[room.id]" @stateUpd="updateRoomList"></Room>
    <AddStateButton @newStateCreated="updateRoomList"/>
  </div>
</template>

<script>
import AddStateButton from '@/components/Add-state-button';
import Room           from '@/components/Room';
import axios          from 'axios';

export default {
  name:       'RoomList', components: { AddStateButton, Room }, data()
  {
    return {
      rooms: [], users: {},
    };
  }, created()
  {
    this.updateData();
    setInterval(this.updateData, 10000);
  }, methods: {
    updateData()
    {
      this.updateRoomList();
      this.updateUserList();
    }, updateRoomList()
    {
      axios.get('http://localhost:3000/rooms').then(response =>
                                                    {
                                                      this.rooms = response.data;
                                                    });
    }, updateUserList()
    {
      axios.get('http://localhost:3000/users').then(response =>
                                                    {
                                                      const data = response.data;
                                                      this.users = {};

                                                      for (const user of data)
                                                      {
                                                        if (this.users[user.room] === undefined)
                                                        {
                                                          this.users[user.room] = [];
                                                        }
                                                        this.users[user.room].push(user);
                                                      }
                                                      console.log(this.users);
                                                    });
    },
  },
};
</script>

<style scoped>

</style>
