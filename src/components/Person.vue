<template>
  <div v-b-tooltip.hover :title="name" class="people">
    <b-icon-person class="icon"></b-icon-person>
    <div>{{ initials }}</div>
  </div>
</template>

<script>
export default {
  name:        'Person', props: {
    person: {
      default: {
        'id': 0, 'firstname': 'Inconnu', 'lastname': 'Inconnu', 'room': 0,
      },
    },
  }, computed: {
    initials()
    {
      return (this.person.firstname[0] + this.person.lastname[0]).toUpperCase();
    }, name()
    {
      return this.person.firstname + ' ' + this.person.lastname.toUpperCase();
    },
  },
};
</script>

<style scoped>
.icon
{
  height: 5vh;
  width:  5vh;
}

.people
{
  cursor: grab;
}
</style>
