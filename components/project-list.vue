<template>
  <div>
    <h2 class="text-2xl font-semibold mb-10">Project</h2>
    
    <section v-if="pending"> Loading...</section>
    <section v-else-if="error">Something went wrong. Try again</section>
    <section v-else>
      <ul class="grid grid-cols-1 gap-4">
        <li v-for="repository in data" :key="repository.id" class=" border border-gray-200 rounded-sm p-4 hover:bg-gray-100 font-mono">
          <a :href="repository.html_url" target="_blank">
            <div class="flex items-center justify-between">
              <div class="font-semibold">{{ repository.name }}</div>
              <div>{{ repository.startgazers_count }} 1</div>
            </div>
            <p class="text-sm">
              {{ repository.description }}
            </p>
          </a>
        </li>
      </ul>
    </section>


  </div>
</template>


<script setup>
  const {error, pending, data} =  await useFetch('https://api.github.com/users/vrigolon/repos');
</script>