<template>
  <div>
    <Message v-for="(msg, index) in messages" :message="msg" :key="index" />
    <button @click="fetchMessages(lastFetchedMessageDate)">Fetch a message</button>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';
import Message from './Message.vue';

export default {
    components: { Message },
    computed: mapGetters(['messages', 'lastFetchedMessageDate']),
    methods: mapActions(['fetchMessages']),
    asyncData ({ store }) {
      return store.dispatch('fetchInitialMessages')
    }
}
</script>
