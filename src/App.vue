<template>
   <div style="padding: 100px" class="app">
      <header>
          <div class="title">
             <h1>Hyrule Jobs</h1>
          </div>
         <div class="order">
            <button @click="handleClick('title')">order by title</button>
            <button @click="handleClick('salary')">order by salary</button>
            <button @click="handleClick('location')">order by location</button>
         </div>
      </header>
     <job-list :jobs="jobs" :order="order"/>
   </div>
</template>

<script lang="ts">


import { defineComponent, reactive, ref, toRefs } from 'vue';
import JobList from './components/JobList.vue';
import Job from './types/job'
import OrderTerm from './types/OrderTerm'

export default defineComponent({
  name: 'App',
  components: {
    JobList

  },
  setup() {
      const jobs = ref<Job[]>([
         { title: 'farm worker', location: 'lon lon ranch', salary: 25000, id: '1' },
         { title: 'quarryman', location: 'death mountain', salary: 30000, id: '2' },
         { title: 'flute player', location: 'the lost woords', salary: 35000, id: '3' },
         { title: 'fisherman', location: 'lake hylia', salary: 40000, id: '4' },
         { title: 'farm worker', location: 'lon lon ranch', salary: 45000, id: '5' }
      ])

      const order = ref<OrderTerm>('title')
      const handleClick = (term: OrderTerm) => {
         order.value = term
      }

      return {jobs, handleClick, order}
  },  
  
   methods: {
      
   }


});
</script>

<style>

header {
   text-align: center;
}

header .order {
   margin-top: 20px;
}

button { 
   margin: 0 10px;
   color: #1195c9;
   border: 3px solid #1195c9;
   background: #d5f0ff;
   padding: 8px 16px;
   border-radius: 4px;
   cursor: pointer;
   font-weight: bold;
}

</style>
