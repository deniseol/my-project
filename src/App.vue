<script>
import ImageNotes from './components/ImageNotes.vue';
import todoImageUrl from './assets/todo_Image.jpg';

export default {
  components: {
    ImageNotes,

  },
  data() {
    return {
      todoImageUrl: todoImageUrl,
    };
  },
};
</script>

<template>
  <div class="flex-container">
    <header>
      <b-navbar class="nav" toggleable="lg" type="dark" >
      <b-navbar-brand id="logo" href="#">ToDo</b-navbar-brand>
        <b-collapse id="nav-collapse" is-nav>
             <b-navbar-nav class="ml-auto">
            <b-nav-item ><RouterLink class="nav-link" to="/">Your list</RouterLink></b-nav-item>
            <b-nav-item><RouterLink class="nav-link" to="/synonyms">Synonyms</RouterLink></b-nav-item>
          </b-navbar-nav>
        </b-collapse>
         <b-navbar-toggle><b-button v-b-toggle:my-collapse id="menu-button">Menu
        </b-button>
        <b-collapse id="my-collapse">
            <b-nav-item ><RouterLink class="nav-link" to="/">Your list</RouterLink></b-nav-item>
            <b-nav-item><RouterLink class="nav-link" to="/synonyms">Synonyms</RouterLink></b-nav-item>
        </b-collapse>
        </b-navbar-toggle>
      </b-navbar>
    </header>
    <main>
        <ImageNotes
        :imageUrl="todoImageUrl"
        altText="To-do list and computer"/>
      <RouterView />
    </main>
    <footer>
      <p class="whiteText">copyright © Denise Olsson</p>
    </footer>
  </div>
</template>

<style>
.flex-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
.collapsed > .when-open,
.not-collapsed > .when-closed {
  display: none;
}
#menu-button {
  text-align: center;
  align-items: center;
  background-color: #f8f9fa;
  border: 1px solid #f8f9fa;
  color: #333;
  width: 60px;
  height: 60px;
}
#my-collapse {
  background-color: #f8f9fa;
  border: 1px solid #f8f9fa;
  color: #333;
}
#menu-button:hover {
  background-color: #e9ecef48;
  border: 1px solid #e9ecef48;
  color: #333;
}
.grid-container {
  display: grid;
  grid-template-rows: auto, 1vh, auto; /* Header, Main, Footer */
  min-height: 100vh;
}
.ml-auto {
    margin-left: calc(100vw/3);
    gap: 100px;
}
.nav {
   color: rgb(196, 255, 175);
   height: 100px;
}
header {
  height: 100px;
  padding-top: 10px;
  background-color: rgb(248, 248, 243);
  text-align: center;
  align-items: center;
   margin: 0%;
   border: 0%;
}
#logo {
    display: flex;
    justify-content: left;
  font-size: 30px;
  color: rgb(37, 12, 2);
  padding: 20px;
}
main {
  background-color: rgba(225, 199, 144, 0.404);
  padding: 20px;
  text-align: center;
  flex: 1;
}
footer {
  background-color: rgb(19, 10, 1);
  padding: 20px;
  text-align: center;
  height: 120px;
  position: bottom;
}
p {
    color: black;
}
.whiteText {
    padding-top: 35px;
    color: white;
}
</style>
