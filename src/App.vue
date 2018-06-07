<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>Witaj w systemie zapisów na zajęcia</h1>

    <div v-if="!authenticatedUsername">
      <login-form @login="logMeIn($event)"></login-form>
    </div>
    <div v-else>
      <logged :authenticatedUsername="authenticatedUsername" @login='logMeOut()'></logged>
      <meeting-page></meeting-page>
    </div>

  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
import Logged from "./Logged";
import MeetingPage from "./meetings/MeetingPage";
import MeetingsList from "./meetings/MeetingsList";
import NewMeetingForm from "./meetings/NewMeetingForm";
export default {
  components: {
    LoginForm,
    Logged,
    MeetingPage,
    MeetingsList,
    NewMeetingForm
  },
  name: 'app',
  data () {
    return {
      authenticatedUsername: ''
    }
  },
  methods: {
    logMeIn(username) {
      this.authenticatedUsername = username;
    },
    logMeOut() {
      this.authenticatedUsername = "";
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>