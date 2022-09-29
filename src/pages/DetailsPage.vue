<template>
  <div class="details" v-if="classified">

    <div class="col-11 " v-if="classified.listingType == 'Car'">
      <SelectedCar :car="classified.listing" :seller="classified.seller" />
    </div>
    <div class="col-11 " v-else-if="classified.listingType == 'Job'">
      <SelectedJob :job="classified.listing" :seller="classified.seller" />
    </div>
    <div class="col-11 " v-else-if="classified.listingType == 'House'">

    </div>
    <i class="mdi mdi-delete-forever fs-4 selectable rounded" @click="deleteClassified(classified.id)"></i>
  </div>
  <div v-else>
    loading...
  </div>
</template>

<script>
import { computed } from '@vue/reactivity';
import { onMounted } from 'vue';
import { useRoute, useRouter } from 'vue-router';
import { AppState } from '../AppState.js';
import CarCard from '../components/CarCard.vue';
import { classifiedsService } from '../services/ClassifiedsService.js';
import Pop from '../utils/Pop.js';
import SelectedCar from '../components/SelectedCar.vue';
import { logger } from '../utils/Logger.js';
import SelectedJob from '../components/SelectedJob.vue';

export default {
  setup() {
    const route = useRoute();
    const router = useRouter();
    async function getClassifiedById() {
      try {
        await classifiedsService.getClassifiedById(route.params.id);
      }
      catch (error) {
        Pop.error("Sorry that listing no longer exists", "[GettingClassified]");
        router.push({ name: "Home" });
      }
    }
    onMounted(() => {
      getClassifiedById();
    });
    return {
      classified: computed(() => AppState.activeClassified),
      account: computed(() => AppState.account),
      classifieds: computed(() => AppState.classifieds),
      deleteClassified() {
        emit('deleteClassified')
      },
      async deleteClassified(id) {
        try {
          logger.log(id)
          const yes = await Pop.confirm('Delete the Listing?')
          if (!yes) { return }
          await classifiedsService.deleteClassified(id)
          router.push({ name: "Home" });
        } catch (error) {
          Pop.error(error, '[Deleting Classified]')
        }
      }
    };
  },
  components: { CarCard, SelectedCar, SelectedJob }
}
</script>
