<template>
  <div class="form">
    <form>
      <label for="fname">Name</label><br>
      <input type="text" v-model="Name" class="nameInp" name="fname" :placeholder="member.Ename">
      <br>
      Select user access level<br>
      <input type="radio" id="Analyst" name="Analyst" value="Analyst" v-model="pos">
      <label for="analyst">Analyst</label><br>
      <input type="radio" id="Admin" name="Admin" value="Admin" v-model="pos">
      <label for="Admin">Admin</label><br>
      <input type="radio" id="Tech Support" name="Tech Support" value="Tech Support" v-model="pos">
      <label for="Tech Support">Tech Support</label><br>
      </form>
      <button class="btn" @click="update()">Update</button>
  </div>
</template>

<script>
export default {
  name: 'EditMember',
  props: {
    member: Object,
  },
  data() {
    return {
      Name: this.member.Ename,
      pos: this.member.pos,
    };
  },
  methods: {
    update() {
      // this.showEdit = !this.showEdit;
      const newMember = {
        Ename: this.Name,
        role: this.pos,
      };
      const newAndOldMem = [];
      newAndOldMem.push(this.member, newMember);
      console.log(newAndOldMem);
      this.$emit('update', newAndOldMem);
    },
  },
  emits: ['update'],
};
</script>

<style>
.btn {
  background-color: rgba(103,36,234,255);
  color: white;
  padding: 10px;
  font-size: 16px;
  border: none;
  float: right;
  margin-right: 10px;
  border-radius: 5px;
  cursor: pointer;
}
.nameImp {
  font: bold;
  font-family: serif;
  font-weight: 400;
}
</style>
