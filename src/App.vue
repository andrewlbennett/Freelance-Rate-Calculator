<template>
    <div id="app">
        <header></header>
        <Calculator/>
        <footer>
            <p>A product made by <a href="https://www.andrewbennett.us" target="_blank">Andrew Bennett</a></p>
            <p>MIT License - Open Source</p>
            <a href="https://github.com/andrewlbennett/Freelance-Rate-Calculator" target="_blank">Github Repo</a>
        </footer>
    </div>
</template>

<script>
import Calculator from "./components/Calculator.vue";

export default {
  name: "app",
  components: {
    Calculator
  }
};
</script>

<style lang="scss">
html, body {
    margin: 0;
}
#app {
    display: flex;
    flex-direction: column;
    font-family: "Roboto", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin: 0;
}
header {
    padding: 3rem;
}
footer {
    margin-top: 150px;
    padding: 3rem 6rem;
    background-color: #f7f7f7;
}
</style>
