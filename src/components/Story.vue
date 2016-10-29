<template>
  <div class="center-content">
    <h3 class="title is-3 title-head">{{ story.title }}</h3>
    <p class="subtitle is-5 body-content">{{ story.body}}</p>
  </div>
</template>

<script>
export default {
  name: 'story',
  props: ['state'],
  computed: {
    story () {
      let vm = this
      return vm.state.storys.find(story => story.id.toString() === vm.$route.params.id.toString())
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.center-content {
  margin-top: 20px;
  margin-bottom: 10px;
  background-color: #ffffff;
  width: 50%;
  margin-left: 25%;
  margin-right: 25%;
  border: 1px solid #d1d1d1;
  padding-left: 20px;
  padding-right: 20px;
  padding-top: 50px;
  padding-bottom: 100px;
}
.title-head {
  line-height: 50px;
}
.body-content {
  line-height: 30px;
}
</style>
