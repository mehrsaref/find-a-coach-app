<template>
  <section>Filter</section>
  <section>
    <div>
      <button>Refresh</button>
      <base-button
        ><router-link to="/register"
          >Register as coach</router-link
        ></base-button
      >
    </div>
    <ul v-if="hasCoaches">
      <CoachItem
        v-for="coach in filteredCoaches"
        :key="coach.id"
        :coach="coach"
      >
        <!-- {{ coach.firstName }}
        {{ coach.lastName }} -->
        <!-- <CoachItem :coach="coach"></CoachItem> -->
      </CoachItem>
    </ul>
    <h3 v-else>No coaches found</h3>
  </section>
</template>

<script>
import CoachItem from '../../components/CoachItem.vue';
import BaseButton from '../../components/ui/BaseButton.vue';
// import BaseCard from '../../components/ui/BaseCard.vue';
export default {
  components: { CoachItem, 
    BaseButton, 
    // BaseCard 
  },
  computed: {
    filteredCoaches() {
      return this.$store.getters['coaches/coaches'];
    },
    hasCoaches() {
      return this.$store.getters['coaches/hasCoaches'];
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

.controls {
  display: flex;
  justify-content: space-between;
}
</style>
