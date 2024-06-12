<script>
import axios from 'axios';
import ProjectCard from './ProjectCard.vue';

export default {
  components: {
    ProjectCard
  },
  data() {
    return {
      currentPageProjects: []
    }
  },
  methods: {
    fetchProject() {
      axios.get('http://127.0.0.1:8000/api/projects')
        .then((response) => {
          console.log(response.data.results.data)
          this.currentPageProjects = response.data.results.data
        })
    }
  },
  created() {
    this.fetchProject()
  }
}

</script>

<template>

  <main>
    <section>
      <div class="container py-5">
        <div class="row">
          <div v-for="project in currentPageProjects" class="col-4 p-3">
            <ProjectCard :item="project"></ProjectCard>
          </div>
        </div>
      </div>

      <div class="container">
        <div class="row">
          <div class="col-auto">
            <span class="fs-4">1</span>
          </div>
        </div>
      </div>

    </section>
  </main>

</template>

<style></style>