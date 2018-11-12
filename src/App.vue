<template>
  <div id="app">
      <b-navbar toggleable="md" type="dark" variant="info">

        <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>

        <b-navbar-brand href="#">Listing Website</b-navbar-brand>

        <b-collapse is-nav id="nav_collapse">

          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">

            <b-nav-form>
              <b-form-input size="sm" class="mr-sm-2" type="text" placeholder="Search"/>
              <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
            </b-nav-form>

          </b-navbar-nav>

        </b-collapse>
      </b-navbar>

  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      listings: []
    };
  },
  mounted() {
    this.loadListings();
  },
  methods: {
    loadListings(){
      var self = this;
      var app_id = "app838WoUK7gksAto";
      var app_key = "key4hPsF3lTzceL6g";
      axios.get(
          "https://api.airtable.com/v0/"+app_id+"/Weekly%20Report?maxRecords=20&view=Main%20View",
          {
              headers: { Authorization: "Bearer "+app_key }
          }
      ).then(function(response){
        console.log(response.data.records);
        self.listings = response.data.records;
      }).catch(function(error){
        console.log(error)
      });
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
