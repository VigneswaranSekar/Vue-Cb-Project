<template>
 <div>
   <br>
   <div v-for="t in tasks" :key="t.Ename" class="card">
      <h2 class="Ename">{{t.Ename}}</h2>
      <DrpButton :member="t" style="float: right" @del="del(t.Ename)"
      @stopEditForm="editBool=false"
      @showEditForm="editBool=true"
      />
      <h2 class="position">{{t.role}}</h2>
  </div>
  <!-- <div class="editform" v-show="editBool">
      <AddMember :member="tempMem"
      />
  </div> -->
 </div>
</template>

<script>

import DrpButton from './DrpButton.vue';

import AddMember from '../forms/AddMember.vue';

export default {
  name: 'Card',
  data() {
    return {
      editBool: false,
      tempMem: {
        Ename: 'Hello',
        role: 'Analyst',
      },
    };
  },
  props: {
    tasks: Array,
  },
  components: {
    DrpButton,
    // AddMember,
  },
  methods: {
    del(Name) {
      this.$emit('delete', Name);
      return true;
    },
    stopEditForm(bool) {
      this.$emit('stopEditForm', false);
      return false;
    },
    showEditForm() {
      this.ediBool = true;
      return true;
    },
    save(member) {
      this.$emit('save', member);
    },
  },
  emits: ['del', 'stopEditForm'],
};
</script>

<style>
.Ename{
    color: black;
}
.position{
    color: #ccccd0;
}
.card {
  text-align: left;
  margin-left: 10%;
  margin-right: 10%;
  padding-left: 20px;
  padding-top: 1px;
  padding-bottom: 10px;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  border-radius: 10px;
}
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}
</style>
