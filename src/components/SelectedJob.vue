<template>
  <div class="SelectedJob my-2">
    <div class="card p-4 d-flex justify-content-evenly ">
      <img class="yo" :src="seller.picture" alt="SellerPicture">
      <h2 class="my-3">{{seller.name}}</h2>
    </div>
    <div class="d-flex flex-column card card-body my-2">
      <div>
        <h3>{{job.company}}</h3>
        <span>{{job.jobTitle}}</span>
      </div>
      <div>
        <span>{{job.rate}}hrs/wk,</span>
        <span> ${{job.hours}}/hr</span>
      </div>
      <hr>
      <p>{{job.description}}</p>
    </div>
    <div>

    </div>

  </div>
</template>


<script>
import { Job } from '../models/Job.js';
import { SellerProfile } from '../models/SellerProfile.js';

export default {
  props: {
    job: { type: Job, required: true },
    seller: { type: SellerProfile, required: true }
  },
  setup() {
    return {}
  }
}
</script>


<style lang="scss" scoped>
.yo {
  height: 30vh;
  width: 30vh;
}
</style>