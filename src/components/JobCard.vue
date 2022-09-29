<template>
  <div class="JobCard card elevation-2">
    <div class="d-flex flex-column justify-content-between card-body">
      <div>
        <h3>{{job.company}}</h3>
        <span>{{job.jobTitle}}</span>
      </div>
      <!-- <span>{{job.jobTitle}}</span> -->
      <div>
        <span>{{job.rate}}hrs/wk,</span>
        <span> ${{job.hours}}/hr</span>
      </div>
    </div>
  </div>
</template>


<script>
import { Job } from '../models/Job.js';
import { SellerProfile } from '../models/SellerProfile.js';

export default {
  props: {
    seller: { type: SellerProfile, required: true },
    job: { type: Job, required: true }
  },
  setup() {
    return {}
  }
}
</script>


<style lang="scss" scoped>
.JobCard {
  height: 27vh;
}
</style>