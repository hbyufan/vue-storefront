<template>
  <section>
    <SfProductCard style="height: 300px"
      :image="image"
      :image-width="imageWidth"
      :image-height="imageHeight"
      :badge-color="badgeColor"
      :title="item.productName"
      :link="link"
      :link-tag="linkTag"
      :wishlist-icon="wishlistIcon"
      :is-on-wishlist-icon="isOnWishlistIcon"
      :is-on-wishlist="isOnWishlist"
      :show-add-to-cart-button="showAddToCartButton"
      :add-to-cart-disabled="addToCartDisabled"
      :is-added-to-cart="isAddedToCart"
      @click:is-added-to-cart="alert('@click:is-added-to-cart')"
      @click:wishlist="alert('@click:wishlist')"
      @click:reviews="alert('@click:reviews')"
    />
    <div >
      <SfButton v-on:click="addOrder()" class="order">Order</SfButton>
    </div>
  </section>
</template>
<script>
import { SfProductCard, SfButton } from "@storefront-ui/vue";
import OrderService from "../_services/order.service";

export default {
  name: "ProductItem",
  components: {
    SfProductCard,
    SfButton
  },
  props: {
    item: Object
  },
  data() {
    return {
      image: {
        mobile: { url: "https://www.meme-arsenal.com/memes/69b5e3c95bd05fe729c7977b6807f017.jpg" },
        desktop: { url: "https://www.meme-arsenal.com/memes/69b5e3c95bd05fe729c7977b6807f017.jpg" }
      },
      imageWidth: 216,
      imageHeight: 326,
      badgeColor: "color-primary",
      link: "",
      linkTag: "",
      wishlistIcon: "heart",
      isOnWishlistIcon: "heart_fill",
      isOnWishlist: false,
      isAddedToCart: false,
      addToCartDisabled: false,
      showAddToCartButton: false
    };
  },
  methods: {

    addOrder() {
      OrderService.createOrder(this.item.productName);
    }
  }
};
</script>
