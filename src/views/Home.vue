<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <NestedList id="mainList" :dataList='{"Home": { "Home__Sub": ["home--1", "home--2", "home--3"]}, "About": ["about--1", "about--2", "about--3"], "Contact": ["contact--1", "contact--2", "contact--3"]}'/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';
import NestedList from '@/components/nested-list.vue';

export default {
  name: 'Home',
  components: {
    HelloWorld,
    NestedList
  }
}
</script>
