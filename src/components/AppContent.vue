<script>
import axios from 'axios';
import ProjectCard from './ProjectCard.vue';

export default {
  components: {
    ProjectCard
  },
  data() {
    return {
      currentPageProjects: [],
      currentPage: 1,
      lastPage: null,
    }
  },
  methods: {
    fetchProjects(n) {
      axios.get('http://127.0.0.1:8000/api/projects', {
        params: {
          page: n
        }
      })
        .then((response) => {
          this.currentPageProjects = response.data.results.data
          this.currentPage = response.data.results.current_page
          this.lastPage = response.data.results.last_page
        })
    }
  },
  created() {
    this.fetchProjects(1)
  }
}

</script>

<template>

  <main>
    <section class="d-flex flex-column justify-content-between align-items-center h-100">
      <div class="container pt-5 flex-grow-1">
        <div class="row h-100">
          <div v-for="project in currentPageProjects" class="col-4 p-3">
            <ProjectCard :item="project"></ProjectCard>
          </div>
        </div>
      </div>

      <div class="btn btn-secondary" @click="console.log(currentPage)">Test</div>

      <div class="container nav-menu">
        <div class="row py-3 justify-content-center align-items-baseline">
          <div class="col-auto">
            <font-awesome-icon :class="currentPage === 1 ? 'nav-btn-disabled' : ''" class="fs-5 nav-btn"
              :icon="['fas', 'angles-left']" @click="fetchProjects(1)" />
          </div>
          <div class="col-auto" @click="">
            <font-awesome-icon :class="currentPage - 1 <= 0 ? 'nav-btn-disabled' : ''" class="fs-5 nav-btn"
              :icon="['fas', 'angle-left']" @click="fetchProjects(currentPage - 1)" />
          </div>
          <div class="col-auto">
            <span class="fs-4">{{ currentPage }}</span>
          </div>
          <div class="col-auto">
            <font-awesome-icon :class="currentPage + 1 > lastPage ? 'nav-btn-disabled' : ''" class="fs-5 nav-btn"
              :icon="['fas', 'angle-right']" @click="fetchProjects(currentPage + 1)" />
          </div>
          <div class="col-auto">
            <font-awesome-icon :class="currentPage + 2 > lastPage ? 'nav-btn-disabled' : ''" class="fs-5 nav-btn"
              :icon="['fas', 'angles-right']" @click="fetchProjects(lastPage)" />
          </div>
        </div>
      </div>

    </section>
  </main>

</template>

<style scoped>
.nav-btn {
  cursor: pointer;
}

.nav-btn:hover {
  color: rgb(84, 177, 231);
}

.nav-btn-disabled {
  cursor: default;
  color: lightgrey;
  pointer-events: none;
}

.nav-menu a {
  color: currentColor;
  text-decoration: none;
}
</style>