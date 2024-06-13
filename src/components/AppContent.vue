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
      <div class="container pt-5">
        <div class="row">
          <div v-for="project in currentPageProjects" class="col-4 p-3">
            <ProjectCard :item="project"></ProjectCard>
          </div>
        </div>
      </div>

      <div class="container">
        <div class="row py-3 justify-content-center align-items-center">
          <div class="col-auto">
            <font-awesome-icon class="fs-5" :icon="['fas', 'angles-left']" />
          </div>
          <div class="col-auto">
            <font-awesome-icon class="fs-5" :icon="['fas', 'angle-left']" />
          </div>
          <div class="col-auto">
            <span class="fs-4">1</span>
          </div>
          <div class="col-auto">
            <font-awesome-icon class="fs-5" :icon="['fas', 'angle-right']" />
          </div>
          <div class="col-auto">
            <font-awesome-icon class="fs-5" :icon="['fas', 'angles-right']" />
          </div>
        </div>
      </div>

    </section>
  </main>

</template>

<style></style>