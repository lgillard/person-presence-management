<template>
  <div>
    <header><h1>Ou-est CharliMT ?</h1></header>
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
</style>
