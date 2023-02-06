<script setup lang="ts">
import type Job from '@/types/job';
import type OrderTerm from '@/types/orderterm';
import { computed } from 'vue';

interface Props {
    jobs: Job[],
    order: OrderTerm
}

const props = defineProps<Props>()

const orderedJobs = computed(() => {
    return [...props.jobs].sort((a: Job , b: Job) => {
        return a[props.order] > b[props.order] ? 1 : - 1
    })
})

</script>

<template>
    <section class="job-list">
        <TransitionGroup name="list" tag="ul">
            <li v-for="job in orderedJobs" :key="job.id">
                <h2>{{ job.title }} in {{ job.location }}</h2>
                <section class="salary">
                    <img src="@/components/icons/rupee.svg" alt="">
                    <p>{{ job.salary }} rupees</p>
                </section>
                <section class="description">
                    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Praesentium laborum necessitatibus autem! Sapiente placeat distinctio rerum? Voluptate non rem saepe nemo harum accusamus tenetur consequuntur, dolorem ducimus deserunt ullam molestiae?</p>
                </section>
            </li>
        </TransitionGroup>
    </section>
</template>

<style scoped>
  .job-list {
    max-width: 960px;
    margin: 40px auto;
  }
  .job-list ul {
    padding: 0;
  }
  .job-list li {
    list-style-type: none;
    background: white;
    padding: 16px;
    margin: 16px 0;
    border-radius: 4px;
  }
  .job-list h2 {
    margin: 0 0 10px;
    text-transform: capitalize;
  }
  .salary {
    display: flex;
  }
  .salary img {
    width: 30px;
  }
  .salary p {
    color: #17bf66;
    font-weight: bold;
    margin: 10px 4px;
  }

  .list-move {
    transition: all 1s;
  }
</style>

