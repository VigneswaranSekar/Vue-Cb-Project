<template>
  <div class="formE">
    <div class="formCont active">
    <form>
      <label for="fname">Name</label><br>
      <input type="text" v-model="Name" class="nameInp" name="fname" :placeholder="Name">
      <br>
      Select user access level<br>
      <input type="radio" id="Analyst" name="Analyst" value="Analyst" v-model="pos">
      <label for="analyst">Analyst</label><br>
      <input type="radio" id="Admin" name="Admin" value="Admin" v-model="pos">
      <label for="Admin">Admin</label><br>
      <input type="radio" id="Tech Support" name="Tech Support" value="Tech Support" v-model="pos">
      <label for="Tech Support">Tech Support</label><br>
      </form>
      <button data-close-button class="btn" @click="update()">Update</button>
      </div>
      <div class="overlay"></div>
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
      this.Name = '';
      this.pos = '';
      const newAndOldMem = [];
      newAndOldMem.push(this.member, newMember);
      console.log(newAndOldMem);
      this.$emit('update', newAndOldMem);
    },
  },
  created: {
    setDef() {
      this.Name = this.member.Ename;
      this.pos = this.member.pos;
    },
  },
  emits: ['update'],
};
</script>

<style>
.formCont {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%) scale(0);
  border-radius: 100px;
  transition: 200ms ease-in-out;
  background-color: rgb(173, 68, 68);

}

.formCont.active {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%) scale(1);
  border-radius: 15px;
  width: 500px;
  height: 500px;
  background-color: white;
}

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

.overlay {
  position: fixed;
  opacity: 0;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: red;
  transition: 200ms ease-in-out;
  pointer-events: none;
}

#overlay-active {
  pointer-events: all;
  opacity: 0;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: black;
  transition: 200ms ease-in-out;
}

.formE {
  opacity: 1;
  background-color:bisque;
}
</style>
