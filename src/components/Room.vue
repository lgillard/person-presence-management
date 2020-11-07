<template>
  <b-card :style="'background-color:' + room.color">
    <b-card-title>{{ room.name }}</b-card-title>
    <b-card-body></b-card-body>
  </b-card>
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
