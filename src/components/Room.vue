<template>
  <div class="col-3">
    <div :style="'background-color:' + roomTemp.color" class="m-2 box">
      <div v-if="!editEnabled">
        <h2>{{ roomTemp.name }}</h2>
        <div>
          <!-- Peoples -->
          <div></div>

          <!-- Icons -->
          <div>
            <b-icon-trash class="icon left-position pointer" @click="deleteRoom"></b-icon-trash>
            <b-icon-pencil class="icon right-position pointer" @click="editEnabled = true"></b-icon-pencil>
          </div>
        </div>
      </div>
      <div v-else>
        <b-form-input v-model="roomTemp.name" type="text"></b-form-input>
        <div>
          <!-- Color picker -->
          <div>
            <label :for="'color-picker-' + room.id">Couleur de fond:</label>
            <b-form-input :id="'color-picker-' + room.id" v-model="roomTemp.color" type="color"/>
          </div>

          <!-- Icons -->
          <div>
            <b-icon-check class="icon left-position pointer" @click="validate"></b-icon-check>
            <b-icon-x class="icon right-position pointer" @click="cancel"></b-icon-x>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name:       'Room', props: {
    room: {
      default: { id: 0, name: '', color: 'grey' },
    },
  }, data()
  {
    return {
      editEnabled: false, roomTemp: Object.assign({}, this.room),
    };
  }, methods: {
    cancel()
    {
      this.roomTemp    = Object.assign({}, this.room);
      this.editEnabled = false;
    }, validate()
    {
      axios.put('http://localhost:3000/rooms/' + this.room.id, this.roomTemp).then(() =>
                                                                                   {
                                                                                     this.$emit('stateUpd');
                                                                                     this.editEnabled = false;
                                                                                   });
    }, deleteRoom()
    {
      axios.delete('http://localhost:3000/rooms/' + this.room.id).then(() =>
                                                                       {
                                                                         this.$emit('stateUpd');
                                                                       });
    },
  },
};
</script>

<style scoped>
.icon
{
  height: 3.5vh;
  width:  3.5vh;
}

.right-position
{
  bottom:   2vh;
  position: absolute;
  right:    4vh;
}

.left-position
{
  bottom:   2vh;
  position: absolute;
  right:    9vh;
}
</style>
