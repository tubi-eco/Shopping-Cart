<template>
  <div id="app">
    <div class="wrapper">
      <Header></Header><br>
      <shopping-list-wrapper :counter ="counter" @counterEvent = "counter += $event"></shopping-list-wrapper>
    </div>
    <Footer></Footer>
  </div>
</template>

<script>
  import Header from "./components/shared/Header";
  import ShoppingListWrapper from "./components/ShoppingListWrapper";
  import Footer from "./components/shared/Footer";

export default {
  name: 'app',
  data () {
    return {
      counter:0
    }
  },
  components : {
    Header,
    ShoppingListWrapper,
    Footer,
  }
}
</script>

<style lang="scss">
html, body, #app {
  height: 100%;
  margin: 0;
  font-family: 'Roboto', sans-serif;
}
.wrapper {
  background: #edf0f1;
  min-height: calc(100% - 80px);
}
.footer,
.push {
  height: 80px;
}
.mobile-hide{
  display: block;
    @media(max-width: 767px){
    display: none;
    }
}

</style>
