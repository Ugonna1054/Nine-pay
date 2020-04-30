<template>
  <div>
    <div class="main-wrapper-1">
      <header>
        <div>
          <b-navbar type="dark" class="main-wrapper" variant>
            <b-navbar-brand href="#">
              <img
                src="../assets/images/logo.jpg"
                class="d-inline-block align-to img-fluid-home ml-0 ml-md-5"
                alt="logo"
                width="60px"
              />
            </b-navbar-brand>

            <b-navbar-toggle
              class="nav-toggle"
              target="nav-collapse"
            ></b-navbar-toggle>

            <b-collapse id="nav-collapse" class is-nav>
              <!-- Right aligned nav items -->
              <b-navbar-nav class="ml-auto nav-bg">
                <b-nav-item class="nav-item" href="#">
                  <span class="text-color">Login</span>
                </b-nav-item>
                <b-nav-item class="nav-item" href="#" @click="ShowLogin = true">
                  <span class="text-color">Signup</span>
                </b-nav-item>
                <b-nav-item
                  class="nav-item"
                  href="#"
                  @click="ShowSignup = true"
                >
                  <span class="text-color join">
                    Need help?
                    <span class="d-none d-sm-inline"></span>
                  </span>
                </b-nav-item>
              </b-navbar-nav>
            </b-collapse>
          </b-navbar>
        </div>
      </header>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      ShowLogin: false,
      ShowSignup: false
    }
  }
}
</script>

<style scoped>
.img-fluid-home {
  margin-left: 0px;
}
.main-wrapper {
  /* background:; */
}

.nav-item {
  color: red !important;
}
.nav-toggle {
  background: #333 !important;
}

.nav-bg {
  padding: 10px;
}

.text-color {
  color: white;
  font-family: Montserrat-Medium;
}

.text-color:hover {
  color: silver;
}
</style>
