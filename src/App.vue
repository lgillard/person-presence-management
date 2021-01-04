<template>
  <div class="page-container">
    <header class="d-flex justify-content-between">
      <h1>Où-est CharliMT ?</h1>
      <ChatIcon></ChatIcon>
    </header>
    <RoomList/>
  </div>
</template>

<script>
import ChatIcon from '@/components/Chat-icon';
import RoomList from '@/components/RoomList';

export default {
  name: 'App', components: {
    ChatIcon, RoomList,
  },
};
</script>

<style>
h1
{
  text-decoration: underline;
}

h2
{
  font-size: 10vh;
}

.page-container
{
  margin: 5vh;
}

.border-1
{
  border: solid 1px;
}

.box
{
  height:     50vh;
  text-align: center;
}

.pointer
{
  cursor: pointer;
}
</style>
