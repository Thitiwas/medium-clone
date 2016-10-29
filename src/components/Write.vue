<template>
  <div class="hello">
    <input class="input-title"  v-model="title" placeholder="Title">
      <textarea class="textarea-content " v-model="body" placeholder="Tell your story..."></textarea>
    <a class="button is-success button-save" @click="addNewStory">
      <span class="icon">
        <i class="fa fa-check"></i>
      </span>
      <span>Save</span>
    </a>
  </div>
</template>

<script>
export default {
  name: 'write',
  props: ['state'],
  data () {
    return {
      title: '',
      body: ''
    }
  },
  methods: {
    addNewStory () {
      let newStory = {
        id: Date.now(),
        title: this.title,
        body: this.body
      }
      this.state.storys.push(newStory)
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
  width: 30%;
  margin-left: 10%;
  margin-right: 60%;
  border: 1px solid #d1d1d1;
  height: 50px;
}
.textarea-content {
  font-size: 20px;
  margin-top: 20px;
  margin-bottom: 10px;
  background-color: #ffffff;
  width: 80%;
  margin-left: 10%;
  margin-right: 10%;
  border: 1px solid #d1d1d1;
  padding-left: 20px;
  padding-right: 20px;
  padding-top: 20px;
  height: 60vh;
  padding-bottom: 100px;
}
.button-save {
  margin-left: 80%;
  width: 10%;
  text-align: center;
  margin-right: 10%;
}
</style>
