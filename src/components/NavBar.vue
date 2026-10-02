<template>
    <!-- navbar -->
    <div class="all">

        <nav class="navbar navbar-expand-lg w-100 ">
            <div class="container-fluid" style="color: #fff;">
                <!-- <a class="navbar-brand" href="#" style="text-decoration: none;"><router-link to="/">
                    <h2>S</h2>
                </router-link>
            </a> -->
                <button class="navbar-toggler text-bg-light" type="button" data-bs-toggle="collapse"
                    data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false"
                    aria-label="Toggle navigation" style="color: #fff !important;">
                    <span class="navbar-toggler-icon" style="color: #fff !important;"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent" style="color: #fff;">
                    <ul class="navbar-nav me-auto mb-2 mb-lg-0" style="display: flex;
                                justify-content: flex-end; z-index: 1;">
                        <li class="nav-item">
                            <a class="nav-link active" aria-current="page" href="#"><router-link
                                    to="/">Home</router-link></a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#"><router-link to="/about">About</router-link></a>
                        </li>
                        <!-- <li class="nav-item">
                            <a class="nav-link" href="#skills"> <router-link to="#skills"
                                    @click="scrollToSection('skills')">Resume</router-link>
                            </a>
                        </li> -->
                        <li class="nav-item">
                            <a class="nav-link "> <router-link to="/projects">Projects</router-link>
                            </a>
                        </li>
                        <li class="nav-item">
              <a class="nav-link">
                <router-link to="/newhome">New Home</router-link>
              </a>
            </li>
                        <li class="nav-item">
                            <a class="nav-link "> <router-link to="/contacts">Contacts</router-link>
                            </a>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>

    </div>
</template>

<script>
export default {

    methods: {
        scrollToSection(anchor) {
            const element = document.getElementById(anchor);
            if (element) {
                element.scrollIntoView({ behavior: 'smooth' });
            }
        },
    },
    // new: Vue({
    //     el: '#all',
    //     data: {
    //         isSticky: false
    //     },
    //     mounted() {
    //         window.addEventListener('scroll', this.handleScroll);
    //     },
    //     methods: {
    //         handleScroll(){
    //             const header = document.getElementById('all');
    //             const headerOffSet = header.offsetTop;

    //             if (window.pageYOffset > headerOffSet) {
    //                 this.isSticky = true
    //             }else{
    //                 this.isSticky = false
    //             }
    //         }
    //     },
    // })
}

</script>

<style scoped>


.navbar {
    display: flex;
    z-index: 1;
    justify-content: space-between;
    width: 100%;
    z-index: 10;
    padding: 5rem 7rem;
    font-family: 'Nunito Sans', sans-serif;
    animation: in 2s ease-in;
}

@keyframes in {
    0% {
        transform: translateX(-100%);
    }

    100% {
        transform: translateX(0%);
    }
}

i {
    display: none;
    align-items: center;
    cursor: pointer;
}

.navbar h2 a {
    text-decoration: none;
}

.navbar h2:hover {
    font-size: 4rem;
}

.navbar ul {
    display: flex;
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

.navbar a:hover{
    color: aqua;
}

.navbar a:hover:active {
    border-bottom: 1px solid aqua;
}

.container-fluid {
    width: 100%;
}

@media (width < 800px) {
    .navbar {
        display: flex;
        justify-content: end;
        z-index: 1;
        width: 100%;
        height: 5rem;
        top: 1rem;
        padding: 0;
        margin: 0 !important;
        font-family: 'Nunito Sans', sans-serif;
        animation: in 1s ease-in;
    }

    .collapse {
        background-color: #171717;
        width: 100%;
        border: 1px solid #ffff;
    }

    .navbar-collapse {
        width: 100%;
        padding-left: 1rem !important;
    }

    .container-fluid {
        width: 100%;
        align-items: end;
        display: flex;
        justify-content: end;
        padding-left: 1rem !important;
    }

}</style>