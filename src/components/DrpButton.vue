<template>
<div class="drp">
  <div class="dropdown">
    <button class="dropbtn">:</button>
    <div class="dropdown-content">
      <button class="but" @click="showEditForm(member)">Edit details</button>
      <button class="but" @click="deleteMem(member.Ename)">Delete member</button>
    </div>
  </div>
</div>
</template>

<script>

import EditMember from '../forms/EditMember.vue';

export default {
  name: 'DrpButton',
  components: {
  },
  props: {
    member: Object,
  },
  methods: {
    deleteMem(Name) {
      console.log(Name);
      this.$emit('del', Name);
      return Name;
    },
    stopEditForm(bool) {
      this.showEdit = false;
      return bool;
    },
    showEditForm(me) {
      this.$emit('showEdit', me);
    },
    updateMem(editmem) {
      this.showEdit = false;
      this.$emit('update-mem', editmem);
    },
  },
  data() {
    return {
      showEdit: false,
    };
  },
  emits: ['stopEditForm', 'update-mem'],
};
</script>

<style>
.dropbtn {
  background-color: rgba(103,36,234,255);
  color: white;
  padding: 14px;
  font-size: 16px;
  border: none;
  cursor: pointer;
  border-radius: 5px;
}
.dropdown {
  position: relative;
  display: inline-block;
}

/* Dropdown Content (Hidden by Default) */
.dropdown-content {
  display: none;
  position: absolute;
  background-color: ccccd0;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0);
  z-index: 1;
}

.dropdown:hover .dropdown-content {
  display: block;
}

/* Change the background color of the dropdown button when the dropdown content is shown */
.dropdown:hover .dropbtn {
  background-color: rgba(103,36,234,255);;
}

.but{
  background-color: rgba(103,36,234,255);
  padding: 5px 3px 5px 3px;
  border-radius: 5px;
  text-align: center;
  color: #dfccf9;
}
</style>
