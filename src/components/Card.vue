<template>
 <div>
   <br>
   <div v-for="t in tasks" :key="t.Ename" class="card">
      <h2 class="Ename">{{t.Ename}}</h2>
      <DrpButton :member="t" style="float: right" @del="del(t.Ename)"
      @showEdit="editform"
      />
      <h2 class="position">{{t.role}}</h2>
  </div>
  <div class="editForm" v-show="editBool">
      <EditMember :member="memToEdit"
      @update="updateMem" />
    </div>
 </div>
</template>

<script>

import DrpButton from './DrpButton.vue';

import EditMember from '../forms/EditMember.vue';

export default {
  name: 'Card',
  data() {
    return {
      editBool: false,
      tempMem: {
        Ename: 'Hello',
        role: 'Analyst',
      },
      memToEdit: {
      },
    };
  },
  props: {
    tasks: Array,
  },
  components: {
    DrpButton,
    EditMember,
  },
  methods: {
    del(Name) {
      this.$emit('delete', Name);
      return true;
    },
    editform(editMem) {
      this.editBool = true;
      this.memToEdit = editMem;
    },
    stopEditForm(bool) {
      this.editBool = false;
      return false;
    },
    showEditForm() {
      this.ediBool = true;
      return true;
    },
    save(member) {
      this.$emit('save', member);
    },
    updateMem(mem) {
      this.editBool = false;
      console.log(mem);
      this.tasks.forEach(function (item, index) {
        if (item.Ename === mem[0].Ename) {
          item.Ename = mem[1].Ename;
          item.pos = mem[1].pos;
          index = 1;
        }
      });
      // this.$emit('update-task', mem);
    },
  },
  emits: ['del', 'stopEditForm', 'update-task'],
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
