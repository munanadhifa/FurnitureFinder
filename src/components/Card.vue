<template>
  <v-app>
    <div class="container">
      <v-row>
        <v-col cols="6" v-for="products in product" :key="products.id">
          <v-card class="mx-auto" max-width="344" outlined>
            <v-list-item three-line>
              <v-list-item-content>
                <div class="overline mb-4" style="font-weight: bold">
                  {{ products.name }}
                </div>
                <v-list-item-subtitle class="desc">{{
                  products.description
                }}</v-list-item-subtitle>
              </v-list-item-content>

              <p class="price">Rp. {{ products.price }}</p>
            </v-list-item>

            <p class="furniture">
              {{ products.furniture_style[0] }}
              {{ products.furniture_style[1] }}
            </p>
            <p class="deliver">{{ products.delivery_time }} Weeks</p>
          </v-card>
        </v-col>
      </v-row>
    </div>
  </v-app>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      product: []
    };
  },

  mounted() {
    var self = this;
    axios.get("http://www.mocky.io/v2/5c9105cb330000112b649af8").then((res) => {
      const product = res.data["products"];
      self.product = [...product];
      console.log(self.product);
    });
  },
};
</script>

<style scoped>
.container {
  width: 900px;
}
.price {
  margin-top: -10px;
  font-size: 14px;
  color: #ffb300;
  font-weight: bold;
}
.desc {
  margin-top: -20px;
}
.furniture {
  margin-left: 15px;
  font-size: 13px;
  color: #42a5f5;
}
.deliver {
  margin-left: 250px;
  font-size: 13px;
  color: #0d47a1;
  font-weight: bold;
}
</style>>

