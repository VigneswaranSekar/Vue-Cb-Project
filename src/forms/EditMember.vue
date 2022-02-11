<template>
  <div class="form">
    <form action="../App.vue" method="POST">
      <label for="fname">Name</label><br>
      <input type="text" v-bind="Name" class="nameInp">
      <br>
      Select user access level<br>
      <input type="radio" id="Analyst" name="Analyst" value="Analyst" v-bind="pos">
      <label for="analyst">Analyst</label><br>
      <input type="radio" id="Admin" name="Admin" value="Admin" v-bind="pos">
      <label for="Admin">Admin</label><br>
      <input type="radio" id="Tech Support" name="Tech Support" value="Tech Support" v-bind="pos">
      <label for="Tech Support">Tech Support</label><br>
      <button class="btn" @click="save()">Save</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'EditMember',
  props: {
    member: Object,
    showEdit: Boolean,
  },
  data() {
    return  {
      Name: '',
      pos: '',
    };
  },
  methods: {
    save() {
      this.showEdit = !this.showEdit;
      return  false;
    },
  },
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
}
</style>
