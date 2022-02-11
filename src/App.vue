<template>
  <div class="app">
  <h1 v-show="dataBool" class="title">
    {{title}} ({{team.length}})
  <button @click="openform()" class="button">+ Invite members</button>
  </h1>
  <br>
    <Card :tasks="team" @delete="del"/>
  </div>
</template>

<script>
import { defineComponent } from '@vue/composition-api';

import Home from './views/Home.vue';

import About from './views/About.vue';

import Card from './components/Card.vue';

export default defineComponent({
  name: 'app',
  data() {
    return {
      dataBool: true,
      team: [],
      title: 'Task Manager',
    };
  },
  methods: {
    toggle() {
      this.dataBool = (!this.dataBool);
      return this.dataBool;
    },
    openform() {
      console.log('open the form');
    },
    del(Name) {
      let i = 0;
      for (i = 0; i < this.team.length; i += 1) {
        if (this.team[i].Ename === Name) {
          console.log('Inside if block');
          console.log(i);
          this.team = this.team.splice(i, 1);
        }
      }
    },
  },
  components: {
    Home,
    About,
    Card,
  },
  created() {
    this.team = [
      {
        Ename: 'Vishwaa',
        role: 'Analyst',
      },
      {
        Ename: 'Rama',
        role: 'Tech Support',
      },
    ];
  },
});
</script>

<style scoped>
 .app{
  background-color: rgba(238,237,246,255);
  text-decoration-color: blue;
  text-decoration-skip: edges;
  padding: 10px 20px;
  margin: auto 10px;
  width: auto;
  height: 2000px;
  cursor: pointer;
}
.button {
  transition-duration: 0.7s;
  color: #dfccf9;
  background-color: rgba(103,36,234,255);
  font-size: 100%;
  padding: 15px 15px;
  border-radius: 35px;
  margin-right: 10%;
  align-content: center;
  margin-left: auto;
  float: right;
}
.button:hover {
  background-color: #21a865;
  color: white;
}
.title{
  font-family: sans-serif;
  color: #282733;

}
.card {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
}
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}
</style>
