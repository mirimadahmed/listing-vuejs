<template>
  <div>
      <b-container>
        <b-row>
            <b-col sm="4" v-for="listing in listings" :key="listing.id">{{listing.fields['Title/Topic']}}</b-col>
        </b-row>
    </b-container>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "Cards",
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