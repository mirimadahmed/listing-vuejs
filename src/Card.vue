<template>
  <div>
      <b-container>
          <b-row>
              <b-col>
                  <h1>
                      Base Heading
                  </h1>
              </b-col>
          </b-row>
          <b-row>
              <b-col sm="8">
                   <b-img src="https://picsum.photos/750/500/?image=41" fluid alt="Responsive image" />
              </b-col>
              <b-col sm="4">
                  <h1>Project Description</h1>
                  <p>Some lorem ispum soda</p>
                  <h1>Project Details</h1>
                  <ul>
                      <li>Some points</li>
                      <li>Some points</li>
                      <li>Some points</li>
                  </ul>
              </b-col>
          </b-row>
          <br><br>
          <b-row>
              <b-col>
                  <h1>Related Projects</h1>
                  <b-container fluid>
                    <b-row>
                        <b-col>
                            <b-img thumbnail fluid src="https://picsum.photos/500/300/?image=54" alt="Thumbnail" />
                        </b-col>
                        <b-col>
                            <b-img thumbnail fluid src="https://picsum.photos/500/300/?image=58" alt="Thumbnail" />
                        </b-col>
                        <b-col>
                            <b-img thumbnail fluid src="https://picsum.photos/500/300/?image=59" alt="Thumbnail" />
                        </b-col>
                        <b-col>
                            <b-img thumbnail fluid src="https://picsum.photos/500/300/?image=59" alt="Thumbnail" />
                        </b-col>
                    </b-row>
                    </b-container>
              </b-col>
          </b-row>
      </b-container>
  </div>
</template>

<script>
export default {
  name: "Card",
  data() {
    return {
    };
  },
  mounted() {
  },
  methods: {
  }
};
</script>