<template>
  <div class="hello">
    <input class="input-title"  v-model="title" placeholder="Title">
      <textarea class="textarea-content " v-model="body" placeholder="Tell your story..."></textarea>
      <div class=""  @click="add">
        <a class="button is-medium button-save">save</a>
      </div>
  </div>
</template>

<script>
export default {
  name: 'write',
  props: ['state', 'addNewStory'],
  data () {
    return {
      title: '',
      body: ''
    }
  },
  methods: {
    add () {
      let newStory = {
        id: Date.now(),
        title: this.title,
        body: this.body
      }
      // this.state.storys.push(newStory)
      this.addNewStory(newStory)
      this.$router.push('/home')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.input-title {
  text-align: center;
  font-size: 20px;
  margin-top: 40px;
  margin-bottom: 10px;
  background-color: #ffffff;
  width: 20%;
  margin-left: 25%;
  margin-right: 55%;
  border: 1px solid #d1d1d1;
  height: 50px;
}
.textarea-content {
  font-family: 'Raleway', sans-serif;
  font-size: 20px;
  margin-top: 20px;
  margin-bottom: 10px;
  background-color: #ffffff;
  width: 50%;
  margin-left: 25%;
  margin-right: 25%;
  border: 1px solid #d1d1d1;
  padding-left: 20px;
  padding-right: 20px;
  padding-top: 20px;
  height: 60vh;
  padding-bottom: 100px;
}
.button-save {
  margin-left: 60%;
  width: 15%;
  margin-right: 25%;
}
</style>
