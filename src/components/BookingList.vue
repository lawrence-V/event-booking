<template>
<template v-if="error">
  <ErrorCard :retry="fetchBookings">Could not load events at the moment Please try again</ErrorCard>  
</template>
<template v-else>
     <section class="grid grid-cols-1 gap-4">  
        <template v-if="!loading"> 
      
          <BookingItem 
          v-for="booking in bookings" 
          :key="booking.id"
          :title="booking.eventTitle" 
          :status="booking.status"
          @cancelled="cancelBooking(booking.id)" />
          </template>
          <template v-else>
            
            <LoadingBookingItem v-for="i in 4" :key="i" />
          </template>
      </section>
</template>
     

  </template>

<script setup>
import {  onMounted } from "vue";



import BookingItem from "./BookingItem.vue";
import LoadingBookingItem from "./LoadingBookingItem.vue";
import useBookings from "../composables/useBookings";
import ErrorCard from "./ErrorCard.vue";
const { bookings,loading,fetchBookings,cancelBooking,error} = useBookings();


onMounted(() => {
  fetchBookings();
});
</script>

<style lang="scss" scoped>

</style>