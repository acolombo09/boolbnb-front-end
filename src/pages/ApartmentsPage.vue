<script>
import axios from 'axios';
import Card from "../components/Card.vue";
import SponsoredApartments from "../components/SponsoredApartments.vue";
import DestinationsCarousel from "../components/DestinationsCarousel.vue";
import FeaturedApartments from "../components/FeaturedApartments.vue";
import { store, filterApartment } from '../store.js';
import LoaderCard from '../components/LoaderCard.vue';

export default {
  data() {
    return {
      store,
      apartments: [],
      amenities: []
    }
  },
  components: {
    Card,
    DestinationsCarousel,
    FeaturedApartments,
    SponsoredApartments,
    LoaderCard
},  
  mounted() {
    filterApartment()

  }
}

</script>

<template>
  <div class="px-0 text-center">

    <!-- Jumbo Section -->
    <div class="text-center jumbotron">
      <div class="d-flex justify-content-center align-items-center h-100 bg-transparent">
        <div class="text-white bg-transparent">
          <h1 class="mb-3 bg-transparent">Welcome to Boolbnb</h1>
          <h4 class="mb-3 bg-transparent">Team 3</h4>
        </div>
      </div>
    </div>

    <!-- Featured Apartments Section -->
    <!-- <FeaturedApartments></FeaturedApartments> -->
    <!-- <SponsoredApartments
    v-if="store.sponsoredList.length > 0">
    </SponsoredApartments> -->

    <!-- Regular Apartments Section -->
    <div class="py-5 px-5 border-bottom" v-if="store.searchLoading === false">
      <h2>Apartments</h2>

      <div class="row row-cols-1 row-cols-md-2 row-cols-lg-4 align-items-stretch g-5 py-3">
        <div class="col px-2" v-for="singleApartment in store.apartments " :key="singleApartment.id">
          <Card :singleApartment="singleApartment"></Card>
        </div>
      </div>
    </div>

    <div class="py-5 px-5 border-bottom" v-if="store.searchLoading === true">
      <h2>Apartments</h2>
      <div class="row row-cols-1 row-cols-md-2 row-cols-lg-4 align-items-stretch g-5 py-3">
        <LoaderCard v-for="index in 12" :key="index" class="col px-2"></LoaderCard>
      </div>
    </div>

    <!-- Trending destinations Section -->
    <DestinationsCarousel></DestinationsCarousel>

    <!-- CTA Section -->
    <div class="py-3 justify-content-center border-bottom">
      <div class="row w-100 my-3 justify-content-center">
        <div class="col text-center pe-0 me-0">
          <div class="card border-0 pe-0 me-0">
            <div class="card-body pe-0 me-0">
              <div class="card-title pe-0 me-0">
                <h3 class="mb-3 pe-0 me-0">News & Discounts</h3>
              </div>
              <div class="row justify-content-center">
                <div class="col-md-4">
                  <p class="color-text">
                    Find your coziest escape ever & Get instant discounts.
                    Discover cabins, vacation homes, and more!
                  </p>
                  <a href="#" class="btn btn-lg btn-primary border-0 mt-2 mb-4">Get in Touch</a><br>
                  <img src="https://i.imgur.com/pC6AgYC.jpg" class="img-fluid" width="450">
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<style lang="scss" scoped>
@use "../scss/partials/_variables.scss" as *;

.color-text {
  color: #757575 !important;
}

button {
  background-color: #3535ec !important;
}

.jumbotron {
  background-image: url('/images/jumbo-img.jpeg');
  height: 450px;
  margin-top: 79px; // header height
  background-size: cover;
  background-position: center;
}

</style>