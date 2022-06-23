<template>
    <nav>
        <router-link to="/">Home</router-link> |
        <router-link to="/about">About</router-link>
    </nav>
    <button type="button" class="btn btn-success">Memes</button>
    <div class="container">
        <list-memes />
    </div>

    <router-view />
</template>

<script>
import ListMemes from "./components/ListMemes.vue";

export default {
    name: "App",
    components: {
        ListMemes,
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

nav {
    padding: 30px;
}

nav a {
    font-weight: bold;
    color: #2c3e50;
}

nav a.router-link-exact-active {
    color: #42b983;
}
</style>
