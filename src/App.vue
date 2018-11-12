<template>
  <div id="app">
      <b-navbar toggleable="md" type="dark" variant="info">

        <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>

        <router-link to="/"><b-navbar-brand>Listing Website</b-navbar-brand></router-link>

        <b-collapse is-nav id="nav_collapse">

          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto" v-if="this.$route.path === '/'">

            <b-nav-form>
              <b-form-input size="sm" class="mr-sm-2" type="text" placeholder="Search" v-model="searchTerm"/>
            </b-nav-form>

          </b-navbar-nav>

        </b-collapse>
      </b-navbar>
      <br><br>
      <router-view ></router-view>

  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      searchTerm: ''
    };
  },
  watch() {
    searchTerm:{
      this.$emit('search', this.searchTerm);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
