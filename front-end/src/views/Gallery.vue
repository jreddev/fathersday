<template>
<div>
  <section class="this">
    <div class="heading">
      <p>Gallery</p>
    </div>
    <div class="image-gallery">
      <div class="image">
        <img src="@/assets/family1.jpg">
        <img src="@/assets/family2.jpg">
        <img src="@/assets/family3.jpg">
        <img src="@/assets/family4.jpg">
        <img src="@/assets/mission.jpg">
        <img src="@/assets/dad1.jpg">
        <img src="@/assets/dadandme.jpg">
        <img src="@/assets/dadandme2.jpg">
        <img src="@/assets/dadandme3.jpg">
        <img src="@/assets/dadandme4.jpg">
        <img src="@/assets/kiss.jpg">
      </div>
    </div>
  </section>
</div>
</template>



<script>
import axios from 'axios';
export default {
  name: 'Gallery',
  components: {
  },
  data() {
    return {

    }
  },
  async created() {
    try {
      let response = await axios.get('/api/users');
      this.$root.$data.user = response.data.user;
    } catch (error) {
      this.$root.$data.user = null;
    }
  },
  computed: {
    user() {
      return this.$root.$data.user;
    }
  },
  methods: {

  }

}
</script>

<style scoped>

.heading {
  padding-top: 20px;
  text-align: center;
}
*,
*:before,
*:after {
  box-sizing: inherit;
}

.image-gallery {
  column-gap: 5px;
}

.image {
  display: block;
  width: 100%;
}

.image img {
  width: 100%;
  padding-bottom: 5px;
}

/* Masonry on large screens */
@media only screen and (min-width: 1024px) {
  .image-gallery {
    column-count: 4;
  }
}

/* Masonry on medium-sized screens */
@media only screen and (max-width: 1023px) and (min-width: 768px) {
  .image-gallery {
    column-count: 3;
  }
}

/* Masonry on small screens */
@media only screen and (max-width: 767px) and (min-width: 540px) {
  .image-gallery {
    column-count: 2;
  }
}

</style>
