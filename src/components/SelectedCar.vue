<template>
  <div class="SelectedCar justify-content-evenly d-flex my-5">
    <div>
      <img class="rounded car" :src="car.imgUrl" :alt="car.make">
    </div>
    <div>
      <div class="my-3">
        <p>{{car.description}}</p>
        <h3>{{car.make}}, {{car.model}}, {{car.year}}</h3>
        <h4>${{car.price}}</h4>
      </div>
      <!-- {{car.id}} -->
      <h2 class="my-3">{{seller.name}}</h2>
      <img :src="seller.picture" alt="SellerPicture">
    </div>
  </div>
  <div class="d-flex justify-content-end">

  </div>
</template>


<script>
import { Car } from '../models/Car.js';
import { SellerProfile } from '../models/SellerProfile.js';

export default {
  props: {
    car: { type: Car, required: true },
    seller: { type: SellerProfile, required: true }
  },
  setup() {
    return {
      // account: computed(() => AppState.account),
      // classifieds: computed(() => AppState.classifieds),
      // deleteClassified() {
      //   emit('deleteClassified')
      // },
      // async deleteClassified(id) {
      //   try {
      //     const yes = await Pop.confirm('Delete the Listing?')
      //     if (!yes) { return }
      //     await classifiedsService.deleteClassified(id)
      //   } catch (error) {
      //     Pop.error(error, '[Deleting Classified]')
      //   }
      // }
    }
  }
}
</script>


<style lang="scss" scoped>
.car {
  height: auto;
  width: 40vw;
  background-size: cover;
  background-position: center;
}
</style>