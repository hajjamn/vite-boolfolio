<script>

export default {
  components: {
  },
  data() {
    return {
    }
  },
  props: {
    item: Object
  },
  craeted() {
    console.log(item)
  }
}

</script>

<template>

  <div class="card h-100">
    <!-- HEADER -->
    <div class="card-header text-center">
      <h3 class="fs-5">{{ item.title }}</h3>
    </div>
    <!-- BODY -->
    <div class="card-body">
      <ul class="list-group mb-4">
        <li class="list-group-item"><a href="#">{{ item.repo }}</a></li>
        <li class="list-group-item">{{ item.type_id }}</li>
      </ul>
      <p>{{ item.description }}</p>
    </div>
    <!-- FOOTER -->
    <div class="card-footer">
      <div class="row">
        <div class="col-auto rounded-circle bg-secondary border border-black">
          <span class="fs-4">{{ item.id }}</span>
        </div>
      </div>
    </div>
  </div>

</template>

<style></style>