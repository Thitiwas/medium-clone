<template>
  <div class="hello">
    <div class="" v-for="story in state.storys">
      <div class="center-column" >
        <router-link :to="{ name: 'story', params: { id:story.id }}">
          <h3 class="title is-3 title-head">{{ story.title }}</h3>
          <p class="subtitle is-5 body-content">{{ story.body.substr(0, 200) }} <br>Read more. . .</p>
        </router-link>
      </div>
      <button class="button-delete" name="button" @click="deleteStory(story.id)">  Delete story</button>
    </div>

  </div>
</template>

<script>
export default {
  name: 'home',
  props: ['state', 'deleteStory'],
  data () {
    return {}
  }
}
</script>
<style scoped>
.center-column {
  font-family: 'Raleway', sans-serif;
  margin-top: 20px;
  margin-bottom: 5px;
  background-color: #ffffff;
  width: 50%;
  margin-left: 25%;
  margin-right: 25%;
  border: 1px solid #d1d1d1;
  padding-left: 20px;
  padding-right: 20px;
  padding-top: 20px;
  padding-bottom: 15px;
}
.title-head {
  line-height: 50px;
  display: inline-block;
}
.body-content {
  line-height: 30px;
}
.button-delete {
  font-family: 'Raleway', sans-serif;
  cursor: pointer;
  font-size: 1.5em;
  color: white;
  border-radius: 10px;
  border: 0px solid;
  background-color: #ff1f4b;
  height: 40px;
  /*width: 15%;*/
  margin-left: 65%;
  margin-right: 25%;
}
</style>
