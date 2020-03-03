<template>
  <div id="app">
    <b-container class="bv-example-row">
      <b-row>
        <b-col>
          <ContactList />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import ContactList from "./components/ContactList.vue";

export default {
  name: "App",
  components: {
    ContactList
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
