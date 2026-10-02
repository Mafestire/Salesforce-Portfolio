<template>
    <nav class="navbar navbar-expand-lg">
      <div class="container-fluid" style="color: #fff">
        <a class="navbar-brand" href="#" style="text-decoration: none"
          ><router-link to="/">
            <h2 style="width: 2rem">S</h2>
          </router-link>
        </a>
        <button
          class="navbar-toggler text-bg-light"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon" style="color: #fff"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul
            class="navbar-nav me-auto mb-2 mb-lg-0"
            style="display: flex; justify-content: flex-end"
          >
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#"
                ><router-link to="/">Home</router-link></a
              >
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#"
                ><router-link to="/about">About</router-link></a
              >
            </li>
            <!-- <li class="nav-item">
              <a class="nav-link" href="#">
                <router-link to="/#skills">Resume</router-link>
              </a>
            </li> -->
            <li class="nav-item">
              <a class="nav-link">
                <router-link to="/projects">Projects</router-link>
              </a>
            </li>
            <!-- <li class="nav-item">
              <a class="nav-link">
                <router-link to="/projects#Testimonials"
                 @click="scrollToSection('Testimonials')" >Testimonials</router-link
                >
              </a>
            </li> -->
            <li class="nav-item">
              <a class="nav-link">
                <router-link to="/contacts">Contacts</router-link>
              </a>
            </li>
            <li class="nav-item">
              <a class="nav-link">
                <router-link to="/newhome">New Home</router-link>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
</template>

<script>
export default {
    methods: {
    scrollToSection(anchor) {
      const element = document.getElementById(anchor);
      if (element) {
        element.scrollIntoView({ behavior: 'smooth'});
      }
    },
  },
};
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-around ;
  width: 100%;
  /*height: 5rem;*/
  /* top: 1rem; */
  z-index: 10;
  padding: 1rem 3rem;
  font-family: "Nunito Sans", sans-serif;
  background-color: #111827;
  /* text-align: end; */
}

button{
  margin-top: -6%;
}

.container-fluid{
  height: 5rem;
  padding: 0 2rem;
  /* display: flex;
  justify-content: space-between !important; */
}

.collapse {
  /* display: flex;
  justify-content: end;
  text-align: end; */
  padding-left: 50%;
}

i {
  display: none;
  align-items: center;
  cursor: pointer;
}

.navbar h2 {
  /* margin-left: 15px; */
  margin-top: 2.5rem !important;
  color: aqua;
  font-size: 3.5rem;
  text-decoration: none;
  /* margin-top: 0rem; */
}

.navbar h2 a {
  text-decoration: none;
}

.navbar h2:hover {
  font-size: 4rem;
}

.navbar ul {
  display: flex;
  text-align: end;
}

.navbar li {
  list-style: none;
  text-decoration: none;
}

.navbar a {
  list-style: none;
  text-decoration: none;
  margin-right: 15px;
  font-size: 1.3rem;
  color: #ffff;
}

.navbar a:hover {
  color: aqua;
}

@media (width < 992px) {
  .navbar {
    /* margin-top: -5rem; */
    /* padding: 0rem 1rem !important; */
    /* transform: translateY(50%); */
    display: flex !important;
    /* justify-content: end; */
  }

  .navbar-expand-lg{
    padding: 0 !important;
  }
  
 button{
  margin-top: 0rem !important;
 }

  span {
    color: aqua;
  }

  .navbar h2{
    margin-top: 1.5rem !important;
  }

  .collapse {
    background-color: #111827;
    width: 100%;
    border: 1px solid #ffff;
    text-align: start;
    /* padding: 1rem 4rem; */
  }
}

@media (width < 500px) {
  .navbar h2 {
    margin-top: 2rem !important;
  }

  button{
    margin-top: -.5rem !important;
  }
}

/* .active{
    border-bottom: 2px solid aqua;
} */
</style>
