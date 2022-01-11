<template>
  <div id="app">
    <ul>
      <li v-for="message in messages">
        {{ message.text }} - {{ message.createdAt }}
        <button @click="deleteMessage(message)">X</button>
      </li>
    </ul>
    <form @:submit.prevent="addMessage">
      <textarea v-model="newMessage" placeholder="Leave a message"></textarea>
      <div><button v-bind:disabled="messages.length >= 10"
                   type="submit">Add</button>
      </div>
    </form>
  </div>
</template>

<script>

export default {
  data: {
    messages: [],
    newMessage:''
  },
  methods: {
    addMessage (event) {
      if (!this.newMessage) {
        return;
      }
      this.messages.push(({ text: this.newMessage, createdAt: new Date() }));
      this.newMessage = '';
    },
    deleteMessage (message) {
      this.messages.splice(this.messages.indexOf(message), 1)
    }
  },
  computed: {
    addDisabled() {
      return this.messages.length >= 10 || this.newMessage.length > 50;
    }
  }
}
</script>

<style>
</style>
