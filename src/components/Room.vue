<template>
  <div class="col-3">
    <div class="m-2" :style="'background-color:' + room.color" style="height: 50vh; text-align: center">
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
      default :{name: "", color: "grey"}
    }
  }
};
</script>

<style scoped>

</style>
