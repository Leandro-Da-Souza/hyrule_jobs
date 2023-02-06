<script setup lang="ts">
import { reactive, ref } from 'vue';
import type Job from '@/types/job';
import type OrderTerm from '@/types/orderterm'
import JobsList from './components/JobsList.vue';

/**
 * reactive example
 */
// const state = reactive({
//   name: 'Link',
//   age: 25 as string | number
// })

// const changeName = (name: string): void => {
//   state.name = name
// }

// const changeAge = (age: number | string): void => {
//   state.age = age
// }

/**
 * ref example
 */
// const name = ref<string>('Link')

// const changeName = (name_input: string): void => {
//   name.value = name_input
// }

// const age = ref<number | string>(25)

// const changeAge = (age_input: number | string): void => {
//   age.value = age_input
// }

const jobs = ref<Job[]>([
  { title: 'farm worker', location: 'lon lon ranch', salary: 3000, id: '1' },
  { title: 'quarryman', location: 'death mountain', salary: 4000, id: '2' },
  { title: 'flute player', location: 'the lost woods', salary: 3500, id: '3' },
  { title: 'princess guard', location: 'hyrule castle', salary: 4200, id: '4' }
])

const order = ref<OrderTerm>('title')

const handleClick = (term: OrderTerm) => {
  order.value = term
}
</script>

<template>
  <main class="app">
    <section class="title">
      <img src="@/components/icons/heart.svg" alt="site-logo">
      <h1>Hyrule Jobs</h1>
    </section>
    <header class="order">
      <button @click="handleClick('title')">Order by title</button>
      <button @click="handleClick('salary')">Order by salary</button>
      <button @click="handleClick('location')">Order by location</button>
    </header>
    <JobsList :jobs="jobs" :order="order"/>
  </main>
</template>

<style scoped>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    font-family: WildBreath;
    font-size: 1.2em;
    color: #1195c9;
    border: 3px solid #1195c9;
    background: #d5f0ff;
    padding: 4px 10px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }

  .title {
    display: flex;
    justify-content: center;
  }

  .title img {
    width: 60px;
    margin-right: 20px;
  }

  .title h1 {
    font-size: 3em;
  }
</style>
