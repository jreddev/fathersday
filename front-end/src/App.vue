<template>
  <div id="app">
      <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="navbar-title">
          <router-link class="dropdown-item" to="/">Happy Father's Day!</router-link>
        </div>
          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
              <span class="navbar-toggler-icon"></span>
          </button>

          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
              <li class="nav-item">
                <router-link class="dropdown-item" to="/gallery">Gallery</router-link>
              </li>
              <li class="nav-item">
                <router-link class="dropdown-item" to="/notes">Kind Notes</router-link>
              </li>
              <li class="nav-item">
              <router-link class="dropdown-item" to="/dashboard">Login/Sign Up</router-link>
              </li>
            </ul>
          </div>
        </nav>

    <div class="content">

    </div>

    <router-view />
    <nav class="navbar fixed-bottom navbar-expand-sm navbar-light bg-light">
      <div class="container-fluid">
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarCollapse" aria-controls="navbarCollapse" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarCollapse">
          <ul class="navbar-nav">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="https://github.com/jreddev/creativeProject.git">GitHub</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="https://lab1.jareddevenport.com/">Jared's Photography</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </div>
</template>




<style>
/* Color scheme: https://paletton.com/#uid=7040u0knHs+edG7jrvYscpiuCk2 */
/* red: #e74c3c
 * blue: #277E8E
 */
body {
  font-family: 'Work Sans', sans-serif;
  font-weight: 300;
  font-size: 13pt;
}

.content {
  min-height: calc(100% - 50px);
}

nav {
  display: flex;
  justify-content: center;

}

h1 {
  color: #fff;
  font-size: 18px;
  margin: 0;
  padding: 15px;
  background: #71AB86;
  box-shadow: 0 1px 1px #999;
}

h2 {
  font-size: 12px;
}


.pure-button-primary {
  background-color: #277E8E;
}
.title-bar {
  text-align: right;
  box-shadow: 0 2px 5px #333;
}
.links-bar {
  height: 31px;
  align-items: center;
  width: 200px;
  background-color: #bbb;
  padding: 10px;
  margin-right: 5%;
  transform: translateY(-50px);
  /*box-shadow: 0 2px 5px #aaa;*/

  border-bottom-right-radius: 200px;

  border-top-right-radius: 200px;
  box-shadow: 0 1px 1px #999;
}
.router-link {
  padding: 0;
}
</style>
