<template>
  <div>
    <Person :draggable="false" :person="message.author"/>
    <div></div>
  </div>
</template>

<script>
import Person from '@/components/Person';

export default {
  name: 'Message', components: { Person }, props: {
    message: {
      default: {
        txt: 'pas de contenu au message', date: new Date(), author: {
          'id': 0, 'firstname': 'Inconnu', 'lastname': 'Inconnu', 'room': 0,
        },
      },
    },
  },
};
</script>

<style scoped>

</style>
