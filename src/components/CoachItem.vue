<template>
  <BaseCard>
    <h1>{{ fullName }}</h1>
    <h4>${{ coach.hourlyRate }}/hour</h4>
    <span v-for="area in coach.areas" :key="area">{{ area }}</span>
    <div class="action">
      <router-link :to="coachContactLink">Contact the coach </router-link>
      <router-link :to="coachDetailsLink">Details</router-link>
    </div>
  </BaseCard>
</template>

<script>
import BaseCard from './ui/BaseCard.vue';

export default {
  components: { BaseCard },
  props: ['coach'],
  computed: {
    fullName() {
      return this.coach.firstName + ' ' + this.coach.lastName;
    },
    coachContactLink() {
      return this.$route.path + '/' + this.coach.id + '/contact';
    },
    coachDetailsLink() {
      return this.$route.path + '/' + this.coach.id;
    },
  },
};
</script>

<style scoped>
li {
  margin: 1rem 0;
  border: 1px solid #424242;
  border-radius: 12px;
  padding: 1rem;
}

h3 {
  font-size: 1.5rem;
}

h3,
h4 {
  margin: 0.5rem 0;
}

div {
  margin: 0.5rem 0;
}

.actions {
  display: flex;
  justify-content: flex-end;
}
</style>
