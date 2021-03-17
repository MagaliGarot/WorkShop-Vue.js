<template>
 <div id="app">
  <main>
    <h1>To Do list</h1>
    <List />
  </main>
 </div>
</template>

<script>
import List from "@/components/List";
export default {
  name: 'App',
  components: {
    List,
  },
};
</script>

<style>

  /* ALL */
  * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
  }

  html {
      width: 100%;
      height: 100%;
  }

  a {
      text-decoration: none;
  }

  h1{
    padding-top:2rem;
    font-size: 6rem;
    font-family: 'Satisfy', cursive;
    color: rgb(251, 113, 0);
  }

  body{
    background-image:url("assets/pixabay.jpg");
    /* background-repeat: no-repeat; */
    background-size: cover;
  }

  #app{
    height: 40%;
    width: 59%;
    text-align:center;
    background-color: rgb(11, 54, 66);
    margin-top: 50px;
    margin-right: auto;
    margin-left: auto;
  }

</style>
