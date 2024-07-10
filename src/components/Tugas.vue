<template>
  <div class="tugas-widget p-4 bg-light rounded shadow">
    <h2 class="widget-title mb-4">Tugas</h2>
    <ul class="list-group">
      <li
        class="list-group-item"
        v-for="task in tasks"
        :key="task.id"
      >
        <a :href="task.link" target="_blank" rel="noopener noreferrer">
          {{ task.name }}
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        { id: 1, name: 'Tugas 1', link: 'https://pbk-tugas1-npm.vercel.app/' },
        { id: 2, name: 'Tugas 2', link: 'https://muhammad-darsik-ibmal.vercel.app/' },
        { id: 3, name: 'Tugas 3', link: 'https://us-tuna-sounds-images.voicemod.net/1e8fa13e-5e8e-4f40-a5df-ef49bff19bc5-1680458319767.png' },
        { id: 4, name: 'Tugas 4', link: 'https://tugas4-imal.vercel.app/' },
        { id: 5, name: 'Tugas 5', link: 'https://tugas5imal.vercel.app/home' },
        { id: 6, name: 'Tugas 6', link: 'https://imal66imal.vercel.app/' },
        { id: 7, name: 'Tugas 7', link: 'https://pinia-imal-ek8z.vercel.app/' },
      ],
    };
  },
};
</script>

<style scoped>
.tugas-widget {
  max-width: 500px;
  margin: 0 auto;
  margin-top: 50px;
}

.widget-title {
  font-size: 24px;
  text-align: center;
}

.list-group {
  margin-top: 20px;
}

.list-group-item {
  font-size: 18px;
}

a {
  text-decoration: none;
  color: #007bff; /* Warna link */
}

a:hover {
  text-decoration: underline;
}
</style>
