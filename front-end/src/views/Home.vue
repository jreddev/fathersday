<template>
<div class="home">
  <div class="main-photo">
    <img src="@/assets/family1.jpg">
  </div>
  <div class="myNote">
    <div class="myNote-heading">
      <p>Happy Father's Day Jake!!</p>
    </div>
    <p>I hope you've had a great day so far! feel free to look a the small gallery and at the page of notes for you!</p>
  </div>
  <div class="card-deck">
<div class="card">
<img class="card-img-top" src="@/assets/pex_cam.jpg" alt="Card image cap">
<div class="card-body">
  <router-link class="dropdown-item" to="/gallery">
  <h5 class="card-title">Gallery</h5>
  </router-link>
</div>
</div>

<div class="card">
<img class="card-img-top" src="@/assets/pex_book.jpg" alt="Card image cap">
<div class="card-body">
  <router-link class="dropdown-item" to="/notes">
  <h5 class="card-title">Kind Notes</h5>
  </router-link>

</div>
</div>
<div class="card">
<img class="card-img-top" src="@/assets/pex_key.jpg" alt="Card image cap">
<div class="card-body">
  <router-link class="dropdown-item" to="/dashboard">
  <h5 class="card-title">Login</h5>
  </router-link>
</div>
</div>
</div>
<div class="space">

</div>
</div>
</template>


<script>
export default {
  name: 'Home',
  components: {
  },
  data() {
    return {

    }
  },
  created() {

  },
  methods: {

  }

}
</script>

<style scoped>
img {
  border: 0;
  margin: 0;
  padding:0;
  width: 100%;
}
.dividing-bar {
  padding: 0;
  margin:0;
  border:0;
  transform: translate(0px, -30px);
  height: 30px;
  background-color: #bbb;
}
.router-link {
  padding: 0;
  margin: 0;
  text-align: left;
}

.space {
  padding: 20px;
}

.card-title {
  text-align: center;
}
.card {
  border: 0;
}
.card-deck {
  margin: 10px;
  margin-top: 25px;
}
.myNote {
  padding: 15px;
  text-align: center;
}
.myNote-heading {
  font-size: 25px;
}


</style>
