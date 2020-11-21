<template>
  <div class="col-3">
    <div class="m-2 box" :style="'background-color:' + room.color">
      <h2>{{ room.name }}</h2>
      <div></div>
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

</style>
