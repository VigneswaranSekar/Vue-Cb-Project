<template>
  <div class="dropdown">
    <button class="dropbtn">:</button>
    <div class="dropdown-content">
      <button class="but" @click="showEditForm()">Edit details</button>
      <button class="but" @click="deleteMem(member.Ename)">Delete member</button>
    </div>
</div>
</template>

<script>

export default {
  name: 'DrpButton',
  props: {
    member: Object,
  },
  methods: {
    toggleEdit() {
      this.showEdit = true;
      return true;
    },
    deleteMem(Name) {
      console.log(Name);
      this.$emit('del', Name);
      return Name;
    },
    stopEditForm(bool) {
      this.showEdit = false;
      return bool;
    },
    showEditForm(bool) {
      this.showEdit = true;
      this.$emit('showEditForm', this.member);
      return bool;
    },
  },
  data() {
    return {
      showEdit: false,
    };
  },
  emits: ['stopEditForm'],
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
