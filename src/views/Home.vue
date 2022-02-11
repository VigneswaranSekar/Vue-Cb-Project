<template>
  <div id="container" class="cont">
    <h1>{{tit}} Home File</h1>
  </div>
</template>

<script>
import { defineComponent } from '@vue/composition-api';

export default defineComponent({
  name: 'Home',
  props: {
    tit: String,
  },
});
</script>

<style>
.cont{
  background-color: pink;
  margin: 40px;
  color: red;
}
</style>
