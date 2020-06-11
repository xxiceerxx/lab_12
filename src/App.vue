<template>
  <div id="app">
    <!-- <h1>{{title}}</h1>
    <app-myworker
      v-bind:name = "name"
      v-bind:surname = "surname"
      v-bind:patronymic = "patronymic"
      v-bind:type = "type"
      v-on:lvUp="type = $event + '+'">
    </app-myworker> -->
    <notebook></notebook>
  </div>
</template>

<script>
// import MyWorker from './components/myworker.vue';
import MyNotebook from './components/notebook.vue';


export default {
  name: 'App',
  components: {
    // appMyworker: MyWorker
    // "app-myworker": MyWorker
    notebook: MyNotebook,
  }
  // data(){
  //   return{
  //     title: "Hello World",
  //     name: "Vasya",
  //     surname: "Vasilyev",
  //     patronymic: "Vasilyevich",
  //     type: "Manager"
  //   }
  // }
}
</script>
<style>

.Mob{
    border: 2px double black;
    border-radius: 20px;
    text-align: center;
    margin-top: 5%;
    margin-left: 30%;
    margin-right: 30%;
    height: 1000px;
    background-color: rgb(26, 27, 26);
    color: rgb(238, 228, 228);
}
</style>
