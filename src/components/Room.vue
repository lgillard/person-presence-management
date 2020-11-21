<template>
  <div class="col-3">
    <div class="m-2 box" :style="'background-color:' + room.color">
      <h2>{{ room.name }}</h2>
      <div>
        <b-icon-pencil class="icon pen-position pointer"></b-icon-pencil>
        <b-icon-trash class="icon trash-position pointer"></b-icon-trash>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Room',
  props: {
    room: {
      default :{id:0, name: "", color: "grey"}
    }
  }
};
</script>

<style scoped>
  .icon {
    width: 3.5vh;
    height: 3.5vh;
  }
  .pen-position {
    position: absolute;
    bottom: 2vh;
    right: 4vh;
  }
  .trash-position {
    position: absolute;
    bottom: 2vh;
    right: 9vh;
  }
</style>
