<template>
  <div class="dropdown" v-show="!showEdit">
    <button class="dropbtn">:</button>
    <div class="dropdown-content">
      <button class="but" @click="editDet(member.Ename)">Edit details</button>
      <button class="but" @click="deleteMem(member.Ename)">Delete member</button>
    </div>
    <!-- <div v-show="showEdit">
      <EditMember :member="this.member" :showEdit="true"/>
    </div> -->
</div>
</template>

<script>

// import EditMember from '../forms/EditMember.vue';

export default {
  // components: { EditMember },
  name: 'DrpButton',
  props: {
    member: Object,
  },
  methods: {
    editDet(Name) {
      console.log(Name);
      return Name;
    },
    deleteMem(Name) {
      console.log(Name);
      this.$emit('del', Name);
      return Name;
    },
  },
  data() {
    return {
      showEdit: false,
    };
  },
};
</script>

<style>
.dropbtn {
  background-color: rgba(103,36,234,255);
  color: white;
  padding: 10px;
  margin-bottom: auto;
  font-size: 16px;
  border: 5px;
  float: right;
  margin-right: 10px;
  border-radius: 5px;
}
.dropdown {
  position: relative;
  display: inline-block;
}
.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f1f1f1;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
}
.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}
.dropdown-content a:hover {
  background-color: #ddd;
  }
.dropdown:hover .dropdown-content {
  display: block;
  }
.dropdown:hover .dropbtn {
  background-color: #8221c4;
  }
</style>
