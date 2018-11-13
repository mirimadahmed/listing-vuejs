<template>
  <div>
        <h1>Filters</h1>
        <b-row>
            <b-col sm="12">
               <b-form-input
                   type="text"
                      v-model="searchText"
                      placeholder="Search">
                  </b-form-input>
              </b-col>
          </b-row>
      <br><br>
  </div>
</template>

<script>
export default {
  name: "filters",
  data() {
    return {
      searchText: '',
    };
  },
  methods: {},
  watch: {
      searchText () {
          this.$emit('searched', this.searchText);
      }
  }
};
</script>