<template>
  <!-- NAVBAR -->
  <Nav />

  <!-- LANDING SECTION -->
  <div class="landing">
    <div class="wel">
      <!-- 🌌 ANIMATED SPACE BACKGROUND -->
      <AnimatedBackground />

      <!-- Content sits above background -->
      <div class="image">
        <img
          src="https://i.postimg.cc/4xgLG7J7/C11-Sibabalwe-Mafestire-1-removebg-preview.png"
          alt=""
        />
      </div>
      <div class="greet">
        <p></p>
        <h1 class="who" style="color: #00a1e0">Sibabalwe Mafestire</h1>
        <h3>
          Salesforce Technical Lead
          <span style="color: #00a1e0" class="h3">|</span>
          Salesforce Administration
          <span style="color: #00a1e0" class="h3">|</span>
          Solution Design & Automation
          <span style="color: #00a1e0" class="h3">|</span>
          Programme & Project Delivery
        </h3>
        <div class="landingLogos">
          <img
            src="https://i.postimg.cc/mhfjBzSr/Salesforce-Logo-removebg-preview.png"
            alt=""
            class="salesforceLogo1"
          />
          <img
            src="https://i.postimg.cc/KjJTs1sR/Trailhead-Logo-removebg-preview.png"
            alt=""
            class="trailheadLogo1"
          />
        </div>
      </div>
    </div>
  </div>

  <!-- ABOUT SECTION -->
  <div class="about"><AboutMe /></div>

  <!-- ABOUT Trailhead -->
  <div><TrailHead /></div>

  <!-- ABOUT Certifications -->
  <div><Certifications /></div>

  <!-- ABOUT WORK EXPERIENCE -->
  <div><WorkExperience /></div>

  <!-- ABOUT Contacts -->
  <div><ContactMe /></div>
</template>

<script>
import Nav from "@/components/Nav.vue";
import AboutMe from "@/components/AboutMe";
import TrailHead from "@/components/TrailHead.vue";
import Certifications from "@/components/Certifications.vue";
import WorkExperience from "@/components/WorkExperience.vue";
import ContactMe from "@/components/ContactMe.vue";
import AnimatedBackground from "@/components/AnimatedBackground.vue"; // 👈 NEW

export default {
  components: {
    Nav,
    AboutMe,
    TrailHead,
    Certifications,
    WorkExperience,
    ContactMe,
    AnimatedBackground, // 👈 NEW
  },
};
</script>

<style lang="scss" scoped>
/* ============ keep everything you already had ============ */

.greet {
  color: #fff;
  text-align: center;
  margin-top: 5rem;
  animation: in 2s ease-in;
  font-family: "Nunito Sans", sans-serif;
  flex: 3;
  position: relative; /* 👈 lift above bg */
  z-index: 1;         /* 👈 */
}

.salesforceLogo1,
.trailheadLogo1 {
  width: 6rem;
}

.hi { font-size: 4rem; }
span { font-size: 3.5rem; }

.wel {
  position: relative;        /* 👈 anchor for the absolute bg */
  background-color: #0a1128;
  overflow: hidden;
  font-family: "Nunito Sans", sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  padding-left: 10rem;
  padding-right: 10rem;
  min-height: 100vh;         /* 👈 ensures the bg has room */
}

.image {
  animation: come 2s ease-in;
  display: flex;
  flex: 2;
  align-items: center;
  position: relative; /* 👈 lift above bg */
  z-index: 1;         /* 👈 */
  align-items: center;
  justify-content: center;
  margin-top: 0;
}

img { width: 22rem; }

/* ...keep ALL your existing media queries unchanged... */
@media (width < 766px) {
  .greet {
    margin-left: auto;
    margin-right: auto;
    margin-top: 1rem;
    font-size: 1.5rem;
    text-align: center;
    padding: 1rem 0rem;
  }
  .hi { font-size: 1.5rem; }
  span { font-size: 1.8rem; }
  .image {
    display: flex;
    align-items: center;
    margin: 0 auto;
  }
  img { width: 12rem; }
  .who { font-size: 2rem; }
  .wel {
    display: flex;
    flex-direction: column-reverse;
  }
}

@media (width > 767px) {
  .greet {
    padding: 1rem 0rem;
    display: flex;
    flex: 3;
    flex-direction: column;
    justify-content: center;
    margin-top: 0rem;
    margin-right: 5rem;
  }
  .who { font-size: 2.2rem; }
  h1 { font-size: 1.2rem; }
  span { font-size: 1.5rem; }
  .image {
    display: flex;
    flex: 2;
    align-items: center;
    margin-top: 1rem;
    justify-content: center;
  }
  .wel { display: flex; flex: 3; }
  .h3 { font-size: 30px; }
}

@media (width > 1010px) {
  .greet { font-size: 1.7rem; padding: 1rem 0rem; flex: 3; }
  .who { font-size: 4rem; }
  .image { display: flex; flex: 2; align-items: center; margin-top: 1rem; flex: 1; }
  span { font-size: 3rem; }
  .wel {
    display: flex;
    flex: 3;
    justify-content: center;
    align-items: center;
    padding-left: 10rem;
    padding-right: 10rem;
    margin-top: 0;
  }
}
</style>