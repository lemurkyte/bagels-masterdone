<template>
  <v-container  fluid id>

     <div fluid id="BgPreview">
        <v-container fluid id="imgContainer">
        </v-container>
    </div>

    <v-row>
      <v-col offset-md="1" md="10">
        <h1>Products</h1>
        <div class="pa-2" id="info">
          <v-simple-table id="menu-table">
            <thead>
              <tr>
                <th></th>
                <th class="text-left" style="width:70%">Name of the item</th>
                <th class="text-left" style="width:100px">Price</th>
                <th class="text-left" style="width:100px">Add to basket</th>
              </tr>
            </thead>


            <tbody>
              <tr v-for="item in menuItems" :key="item.name">
                <td id="td_menuitem_img">
                  <v-img v-bind:src="item.image"></v-img>
                </td>
                <td>
                  <span id="td_name">{{ item.name }}</span>
                  <br />
                  <span id="menu_item_description">{{ item.description }}</span>
                </td>
                <td>{{ item.price }}</td>
                <td>
                  <v-btn small text v-on:click="addToBasket(item)">
                    <v-icon color="orange">add_box</v-icon>
                  </v-btn>
                </td>
              </tr>
            </tbody>

          </v-simple-table>
        </div>
      </v-col>

      <!-- BASKET -->

         <!-- END OF THE BASKET -->
    </v-row>
  </v-container>
</template>

<script>


import {dbMenuAdd} from '../../firebase'

export default {
  data() {
    return {
      basketDump:[],
  
    }
  },
  beforeCreate(){
    this.$store.dispatch('setMenuItems')
  },
  methods: {
    addCheckoutItem() {
      this.$store.dispatch('setCheckoutItem')
    },
    addToBasket(item) {
  /*    if (this.basket.find(itemInArray => item.name === itemInArray.name)) {
        item = this.basket.find(itemInArray => item.name === itemInArray.name);
        this.increaseQtn(item);
      } else {
        this.basket.push({
          name: item.name,
          price: item.price,
          quantity: 1
        });
      } */
      this.basketDump.push({
          name: item.name,
          price: item.price,
          quantity: 1
        });
        this.$store.commit('addBasketItems', this.basketDump);
        this.basketDump = [];
    },
    increaseQtn(item) {
      item.quantity++;
    },
    decreaseQtn(item) {
      item.quantity--;

      if (item.quantity === 0) {
        this.basket.splice(this.basket.indexOf(item), 1);
      }
    }
  },
  computed: {
      basket() {
       // return this.$store.state.basketItems
       return this.$store.getters.getBasketItems
      },
      menuItems(){
        return this.$store.getters.getMenuItems
      },
      subTotal () {
          var subCost = 0;
          for( var items in this.basket) {
              var individualItem = this.basket[items];
              subCost += individualItem.quantity * individualItem.price;
          }
          return subCost
      },
      total () {
          var deliveryPrice = 10;
          var totalCost = this.subTotal
          return totalCost + deliveryPrice
      }
  }
};
</script>




<style lang="scss" scoped>
#BgPreview {
    background-image: url("../assets/cover.jpeg");
    background-repeat: no-repeat;
    background-size: cover;
    height: 60vh;
  
}

.col h1 {
  @include infobox_mixin(
    5px,
    map-get($colorz, white),
    10px,
    5px,
    map-get($colorz, white)
  );
  font-weight: bold;
  text-transform: uppercase;
  font-size: 16px;
  text-align: right;
}
.col:last-child h1 {
  text-align: left;
}
#info {
  background-color: white;
}
tr th {
  font-weight: 300;
}
#td_name {
  font-weight: bold;
}
tr td {
  padding: 10px 10px 10px 16px;
}
#menu_item_description {
  font-style: italic;
  font-weight: 300;
  color: map-get($colorz, darkgrey);
  font-size: 13px;
}
#td_menuitem_img{
  max-width: 40px;
  max-height: 40px;
  padding:0;
}
#basket_checkout {
  font-size: 13px;
}
#basket_checkout p:first-child {
  line-height: 2px;
}
</style>