<template>
  <div id="app">
    <nav class="nav headder">
      <div class="nav-left">
        <div class="nav-item is-brand" >
          <router-link class="nav-a" to="/home"><h2 class="title is-2">Medium Clone</h2></router-link>

        </div>
      </div>
      <div class="nav-right nav-menu">
        <a class="nav-item">
          <router-link class="nav-a" to="/home">Home</router-link>
        </a>
        <a class="nav-item">
          <router-link class="nav-a" to="/write">Write</router-link>
        </a>
        <a class="nav-item"></a>
      </div>
    </nav>
        <router-view :state="state" :add-new-story="addNewStory" :delete-story="deleteStory"></router-view>
    </div>
  </div>
</template>

<script>
import firebase from 'firebase'
var config = {
  apiKey: 'AIzaSyBerDiW4RJmvxjVGlpWq3y_GIpmE6IkMPw',
  authDomain: 'medium-clone.firebaseapp.com',
  databaseURL: 'https://medium-clone.firebaseio.com',
  storageBucket: 'medium-clone.appspot.com',
  messagingSenderId: '1066519793292'
}
firebase.initializeApp(config)
var Storys = firebase.database().ref('storys')

export default {
  name: 'app',
  mounted () {
    this.$router.push('/home')
    var vm = this
    Storys.on('child_added', function (data) {
      var item = data.val()
      item.id = data.key
      vm.state.storys.push(item)
    })
    Storys.on('child_removed', function (data) {
      var id = data.key
      var index = vm.state.storys.findIndex(story => story.id === id)
      vm.state.storys.splice(index, 1)
    })
  },
  data () {
    return {
      state: {
        storys: []
      }
    }
  },
  methods: {
    addNewStory (newStory) {
      Storys.push(newStory)
    },
    deleteStory (id) {
      firebase.database().ref('storys/' + id).remove()
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Raleway');
#app {
  background-color: #fafafa;
  height: 100vh;
}
.nav-menu {
  margin-right: 50px;

}
.headder {
  background-color: #2eb778;
  margin-bottom: 50px;
}
.nav-a {
  height: 50px;
  padding-top: 10px;
  font-size: 19px;
  margin-right: 20px;
}
</style>
