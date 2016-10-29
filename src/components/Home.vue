<template>
  <div class="hello">
    <div class="center-column" v-for="story in state.storys">
      <router-link :to="{ name: 'story', params: { id:story.id }}">
        <h3 class="title is-3 title-head">{{ story.title }}</h3>
        <p class="subtitle is-5 body-content">{{ story.body.substr(0, 200) }} <br>Read more. . .</p>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'home',
  props: ['state'],
  data () {
    return {}
  }
}
</script>
<style scoped>
.center-column {
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
  padding-bottom: 20px;
}
.title-head {
  line-height: 50px;
}
.body-content {
  line-height: 30px;
}
</style>
