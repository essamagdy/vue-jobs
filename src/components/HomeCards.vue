<script setup>
import Card from '@/components/Card.vue';
import { RouterLink } from 'vue-router';
</script>


<template>
  <section class="py-4">
      <div class="container-xl lg:container m-auto">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 p-4 rounded-lg">
          <Card>
            <h2 class="text-2xl font-bold">للمطورين</h2>
            <p class="mt-2 mb-4">
              ابحث عن وظيفه و ابدأ حياتك العمليه الان 
            </p>
            <RouterLink
              to="/jobs"
              class="inline-block bg-black text-white rounded-lg px-4 py-2 hover:bg-gray-700"
            >
              Browse Jobs
            </RouterLink>
          </Card>
          <Card>
            <h2 class="text-2xl font-bold">للتوظيف</h2>
            <p class="mt-2 mb-4">
              ضع طلب لأيجاد عمل لك
            </p>
            <RouterLink
              to="/job/add"
              class="inline-block bg-green-500 text-white rounded-lg px-4 py-2 hover:bg-green-600"
            >
              Add Job
            </RouterLink>
          </Card>
        </div>
      </div>
    </section>

</template>