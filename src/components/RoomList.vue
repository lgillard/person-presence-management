<template>
  <div class="row">
    <Room v-for="room in rooms" :key="room.id" :room="room" :users="usersInRoom[room.id]" @stateUpd="updateRoomList"></Room>
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
      rooms: [], users: {}, usersInRoom: {},
    };
  }, created()
  {
    this.initDragAndDropListeners();
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
                                                      const data       = response.data;
                                                      this.usersInRoom = {};
                                                      this.users       = {};

                                                      for (const user of data)
                                                      {
                                                        if (this.usersInRoom[user.room] === undefined)
                                                        {
                                                          this.usersInRoom[user.room] = [];
                                                        }
                                                        this.usersInRoom[user.room].push(user);
                                                        this.users[user.id] = user;
                                                      }
                                                    });
    }, initDragAndDropListeners()
    {
      let personDraggedId;

      document.addEventListener('dragstart', (event) =>
      {
        // store a ref. on the dragged elem
        personDraggedId            = event.target.attributes['data-id'].value;
        // make it half transparent
        event.target.style.opacity = .5;
      }, false);

      document.addEventListener('dragend', (event) =>
      {
        // reset the transparency
        event.target.style.opacity = '';
      }, false);

      /* events fired on the drop targets */
      document.addEventListener('dragover', (event) =>
      {
        // prevent default to allow drop
        event.preventDefault();
      }, false);

      document.addEventListener('drop', (event) =>
      {
        // prevent default action (open as link for some elements)
        event.preventDefault();

        // move dragged elem to the selected drop target
        if (event.target.className.indexOf('dropzone') >= 0)
        {
          const roomId   = event.target.attributes['data-id'].value;
          const userData = Object.assign(this.users[personDraggedId], { room: roomId });

          axios.put('http://localhost:3000/users/' + personDraggedId, userData).then(() =>
                                                                                     {
                                                                                       personDraggedId = '';
                                                                                       this.updateUserList();
                                                                                     });
        }
      }, false);
    },
  },
};
</script>

<style scoped>

</style>
