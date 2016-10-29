<template>
  <div class="hello">
    <div class="center-column" v-for="story in state.storys">
      <router-link :to="{ name: 'story', params: { id:story.id }}">
        <h3 class="title is-3 title-head">{{ story.title }}</h3>
        <p class="subtitle is-5 body-content">{{ story.body.substr(0, 200) }} <br>Read more. . .</p>
      </router-link>
      <div class="control is-grouped  button-delete">
       <p class="control">
        <a class="button is-danger" @click="deleteStory(story.id)">
          Delete story
        </a>
      </p>
      </div>
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
  margin-bottom: 10px;
  background-color: #ffffff;
  width: 50%;
  margin-left: 25%;
  margin-right: 25%;
  border: 1px solid #d1d1d1;
  padding-left: 20px;
  /*padding-right: 20px;*/
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
  width: 15%;
  margin-left: 85%;
  margin-right: 0%;
}
</style>
