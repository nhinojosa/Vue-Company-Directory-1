<script setup>
    import { faker } from '@faker-js/faker'

    const fullName =faker.name.fullName()

    /*
    const firstName =faker.name.fullName()          <------- THIS WORKS TOO ALL TOGETHER
    const lastName =faker.name.lastName()           <------- THIS WORKS TOO ALL TOGETHER
    const fullName = '${firstName} ${lastName}'     <------- THIS WORKS TOO ALL TOGETHER
    */

    /*Use code above instead of line 4 */
   
   /* 
    const firstName =faker.name.fullName()         
    const lastName =faker.name.lastName()           <----- DO NOT USE THIS CODE
    const fullName = '${firstName} ${lastName}'     <----- Professor might have another way.
    */
    const selectCard = () => {
     console.log('${fullName} selected')
    }
    </script>


<template>

    <div class="card" @click="selectCard">
     <div class="card-image">
      <img :src="faker.internet.avatar()" alt="" srcset="" />
     </div>
    <!-- use div for divide -->
    <!-- We did not use "div" anymore -->
    <!-- <div> -->
     <div class="card-details">
       <p class="card-details-name">{{ fullName }}</p>
       <p class="card-details-job">{{ faker.name.jobTitle() }}, {{ faker.name.jobArea() }} </p>
       <p class="card-details-quote">"{{ faker.lorem.paragraph() }}"</p>
     </div>
    <!-- </div>-->
    <!-- remember to comment out "div"-->
    <!-- All  elements inside div are the element-->
    </div>
</template>

<style scoped lang="postcss">

.card {
     
    @apply cursor-pointer overflow-hidden rounded-md bg-slate-100 p-8 shadow-md 
    transition-transform duration-300 
    hover:scale-110 hover:shadow-2xl hover:shadow-blue-900;
    &-image {
        img {
        @apply mx-auto rounded-full object-contain;
        }
    }
    &-details {
        @apply flex flex-col gap-4 pr-6 text-center;
        &-name {
            @apply text-3xl font-thin tracking-wider text-slate-800;
        }

        &-job {
            @apply -mt-2 text-xs text-blue-700;
        }
        

         &-quote {
            @apply pr-4 text-lg italic text-slate-800;
         }
        
    }
}

</style>