<template>
  <div id="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>
    <JobsList :jobs='jobs' :order="order"/>
  </div>
</template>

<script lang="ts">


import { defineComponent, reactive,ref, toRefs } from 'vue';
import JobsList from "@/components/JobsList.vue";
import Job from "./types/Job"
import OrderTerm from "@/types/OrderTerm";

export default defineComponent({
  name: 'App',
  components: {
    JobsList
  },

  setup(){
//=========================================== REACTIVE ==================================================
    // const state = reactive({
    //   name: "Link",
    //   age: 25 as string | number,
    // })
    // state.name = 99; // cannot change type
    // state.age = 27
    // return { ...toRefs(state) }
//========================================= REFS =======================================================
    // const name = ref("Link");
    // const age = ref<number | string>(25);
    //
    // return {name, age}

    const jobs = ref<Job[]>([
      {title: 'farm worker', location: "lon lon ranch", salary: 30000, id: '1'},
      {title: 'quarryman', location: "death mountain", salary: 40000, id: '2'},
      {title: 'flute player', location: "home", salary: 35000, id: '3'},
      {title: 'fisherman', location: "lake eltsovka", salary: 21000, id: "4"},
      {title: 'prison guard', location: "gerudo valley", salary: 32000, id: '5'},
    ])
    const order = ref<OrderTerm>("title")

    const handleClick = (term: OrderTerm) =>{
        order.value = term;
    }

    return {jobs, handleClick, order};
  },
//============================================ DATA ========================================================
  // data(){
  //   return{
  //     name: 'Link',
  //     age: 20 as number | string,
  //   }
  // },
   methods: {

  },
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
