<template>
  <v-app>
    <div class="container">
      <div class="search">
        <v-text-field label="Search Furniture" single-line dark></v-text-field>
      </div>
      <div>
        <v-row>
          <v-col  class="filter-furniture">
            <v-select
              :items="furniture"
              :menu-props="{ maxHeight: '400' }"
              label="Furniture Styles"
              multiple
              solo
              style="width:350px"
            ></v-select>
          </v-col>

          <v-col >
            <v-select
              :items="delivery | deliv('delivery_time')"  
              :menu-props="{ maxHeight: '400' }"
              label="Delivery Time"
              multiple
              solo
              style="width:350px"
            ></v-select>
          </v-col>
        </v-row>
      </div>
    </div>
  </v-app>
</template>

<script>
import axios from "axios";
import Vue from 'vue';

Vue.filter('deliv', function (objects, key) {
    return objects.map(function(object) { 
        return object[key];
    });
});

export default {
  data() {
    return {
      furniture: [],
      delivery: [],
    };
  },

  mounted() {
    var self = this;
    axios.get("http://www.mocky.io/v2/5c9105cb330000112b649af8").then((res) => {
      const furniture = res.data["furniture_styles"];
      self.furniture = [...furniture];
      console.log(self.furniture);

      const delivery = res.data["products"];
      self.delivery = [...delivery];
      console.log(self.delivery);
    });
  },
};
</script>

<style scoped>
.container {
  background-color: #2962ff;
  margin-top: 20px;
  width: 900px;
  height:200px
}
.search {
  width: 350px;
  margin-left: 30px;
  margin-top: 40px;
}
.filter-furniture {
 width: 270px;
margin-left: 30px;
}
</style>
