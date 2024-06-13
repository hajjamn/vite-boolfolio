<script>

export default {
  components: {
  },
  data() {
    return {
      hover: false,
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

<!-- Le Card avranno il Titolo del proj nell'header, I tag nel footer e nel body uno screenshot del proj che in hover mostrera` opacita` con descrizione in bianco in basso e nel centro icona di github con link al progetto. Far muovere un po' la position dell'immagine sarebbe carino -->

<template>

  <div class="card h-100">
    <!-- HEADER -->

    <div class="card-header text-center">
      <h3 class="fs-5">{{ item.title }}</h3>
    </div>

    <!-- BODY -->

    <div class="card-body text-center" :style="{ backgroundImage: `url(https://picsum.photos/320/340)` }"
      @mouseover="hover = true" @mouseleave="hover = false">
      <div class="my-overlay" :class="hover === true ? 'my-active' : ''">
        <div>
          <a :href="item.repo">
            <font-awesome-icon class="text-white fs-2" :icon="['fab', 'github']" />
          </a>
        </div>
        <p class="position-absolute bottom-0">{{ item.description }}</p>
      </div>
    </div>


    <!-- FOOTER -->
    <div class="card-footer">
      <div class="row">
        <div class="col-auto">
          <span>{{ item.type_id }}</span>
        </div>
        <div class="col-auto">
          <span>Technologies placeholder</span>
        </div>
      </div>
    </div>
  </div>

</template>

<style scoped>
.card-body {
  background-size: cover;
  background-position: center center;
  padding: 0 !important;
  position: relative;
}

.my-overlay {
  height: 100%;
  width: 100%;
  position: absolute;
  background-color: rgba(0, 0, 0, 0.5);
  color: white;
  opacity: 0;
  transition: opacity 0.5s ease-in-out;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.my-active {
  opacity: 1;

}
</style>