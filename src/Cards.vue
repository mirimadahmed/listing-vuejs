<template>
  <div>
      <b-container>
        <b-row>
          <filters></filters>
        </b-row>
        <b-row>
            <b-col sm="4" v-for="(listing, i) in listings" :key="i" @click="openListing(i)">
                <b-card :title="listing.fields['Title/Topic'].substring(0,20)"
                    :img-src="getImageUrl(i)"
                    img-alt="Image"
                    img-top
                    tag="article"
                    style="max-width: 20rem;"
                    class="mb-2">
                    <p class="card-text">
                        {{listing.fields.Clipping.substring(0, 50)}}
                    </p>
                </b-card>
            </b-col>
        </b-row>
    </b-container>
  </div>
</template>

<script>
import axios from 'axios';
import Filters from './Filters.vue';
export default {
  name: "Cards",
  components: {Filters},
  data() {
    return {
      listings: []
    };
  },
  mounted() {
    this.loadListings();
  },
  methods: {
    searchIt (){
      console.log($event.payload);
    },
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
    },
    getImageUrl(id){
        if(this.listings[id].fields.Attachment)
            return this.listings[id].fields.Attachment[0].thumbnails.large.url
        else
            return 'https://picsum.photos/600/300/?image=25'
    },
    openListing(id){
        this.$router.push({ name: 'Listing', params: { id: this.listings[id].id }})
    }
  }
};
</script>