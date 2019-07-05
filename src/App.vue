<template>
  <div id="app">
    <todo-list :shouldShowContent="false">
      <template slot="title">
        <h1>I`m the text from parent Component</h1>
      </template>
      <template slot="content">
        <div>
          What is Lorem Ipsum?
          Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.
        </div>
      </template>
    </todo-list>
    <users-list>
      <template slot-scope="slotProps">
        {{ slotProps.user | exitCheck }}
      </template>
      <template slot.score="slotProps">
        
      </template>
    </users-list>
    <div>{{ (message,message1) | capitalize(message,message1) }}</div>
    <div v-for="(user, index) in users" :key="index">
      <NewComp>
        <template slot="username">{{ user.name + ' ' }}</template>
        <template>middle template</template>
        <template slot="exit"> {{ user | exitCheck }} </template>
      </NewComp>
    </div>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import TodoList from "./components/TodoList";
import UsersList from "./components/UsersList";
import NewComp from './components/NewComp'

export default {
  name: "app",
  components: {
    HelloWorld,
    TodoList,
    UsersList,
    NewComp
  },
  data() {
    return {
      message: "Ovo je poruka",
      message1: 'Ovo je druga poruka',
      users: [
        { name: "Misa", isGoingToExit: false },
        { name: "Vojin", isGoingToExit: false },
        { name: "Jelena", isGoingToExit: true },
        { name: "Savic", isGoingToExit: false },
        { name: "Boris", isGoingToExit: false },
        { name: "Nenad", isGoingToExit: false },
        { name: "Andrija", isGoingToExit: false },
        { name: "Milos", isGoingToExit: true },
        { name: "Branko", isGoingToExit: false },
        { name: "Dragana", isGoingToExit: false },
        { name: "Goran", isGoingToExit: false },
        { name: "Vuk", isGoingToExit: false },
        { name: "Vanja", isGoingToExit: true }
      ]
    };
  },

  filters: {
    capitalize: function(value,value1) {
      if (!value) {
        return "";
      }
      value = value.toString();
      return value.charAt(0).toUpperCase() + value.slice(1)+ ' ' + value1.charAt(0).toUpperCase() + value1.slice(1)
    },
    toLowerCase: function(value) {
      if (!value) {
        return "";
      }
      value = value.toString();
      return value.charAt(0).toUpperCase() + value.slice(1);
    },
    
    
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
