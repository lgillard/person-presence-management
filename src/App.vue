<template>
  <div class="page-container">
    <header><h1>Où-est CharliMT ?</h1></header>
    <RoomList/>
  </div>
</template>

<script>
import RoomList   from '@/components/RoomList';

export default {
  name: 'App',
  components: {
    RoomList,
  }
}
</script>

<style>
h1 {
  text-decoration: underline;
}
h2 {
  font-size: 10vh;
}
.page-container {
  margin: 5vh;
}
.border-1 {
  border: solid 1px;
}
.box {
  height: 50vh;
  text-align: center;
}
.pointercrea {
  cursor: pointer;
}
</style>
