<template>
  <header>
    <h1>{{ title }}</h1>
    <Button @click="onclick()" text="Add task" color="Purple"/>
  </header>
</template>

<script>
import Button from './Button';

export default {
  name: "Header",
  props: {
    title: String
  },
  components:{
    Button
  },
  methods:{
    onclick(){
        console.log("Clicked Add Button");
    }
  }
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
