<template>
  <div class="app">
  <h1  class="title">
    {{title}} ({{team.length}})
  <button @click="toggleOn()" class="button">+ Invite members</button>
  </h1>
  <br>
    <Card :tasks="team" @delete="del" @save="save(newMember)" /> <br>
    <AddMember v-show="showAdd" :member="def"
    @save="save(newMember)" />
  </div>
</template>

<script>
import { defineComponent } from '@vue/composition-api';

import Home from './views/Home.vue';

import Card from './components/Card.vue';

import AddMember from './forms/AddMember.vue';

export default defineComponent({
  name: 'app',
  data() {
    return {
      title: 'Task Manager',
      team: [],
      def: {
        Ename: 'Enter name',
        role: 'Enter role',
      },
      showAdd: false,
    };
  },
  computed: {
    dataBool() {
      return this.showAdd;
    },
  },
  methods: {
    toggleOn() {
      this.showAdd = true;
      return this.showAdd;
    },
    del(Name) {
      this.team = this.team.filter((t) => t.Ename !== Name);
    },
    save(newMember) {
      this.team = this.team.push(newMember);
      console.log(this.team);
    },
  },
  components: {
    Home,
    Card,
    AddMember,
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
  transition-duration: 0.3s;
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
