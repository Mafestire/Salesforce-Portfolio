<template>
   <!-- NAVBAR */ -->
    <Nav />

    <!--LANDING SECTION-->>
<div class="landing">
        <div class="wel">
            <div class="image">
                <img src="https://i.postimg.cc/4xgLG7J7/C11-Sibabalwe-Mafestire-1-removebg-preview.png" alt="">
            </div>
            <div class="greet">
                <!--<h1 class="hi"><span>Hello,</span> I am</h1>-->
                <p></p>
                <h1 class="who" style="color: #00A1E0;">Sibabalwe Mafestire</h1>
                <h3>Salesforce Technical Lead <span style="color: #00A1E0;" class="h3">|</span> Salesforce Administration <span style="color: #00A1E0;" class="h3">|</span> Solution Design & Automation <span style="color: #00A1E0;" class="h3">|</span> Programme & Project Delivery</h3>
                <div class="landingLogos">
                    <img src="https://i.postimg.cc/mhfjBzSr/Salesforce-Logo-removebg-preview.png" alt="" class="salesforceLogo1">
                    <img src="https://i.postimg.cc/KjJTs1sR/Trailhead-Logo-removebg-preview.png" alt="" class="trailheadLogo1">
                </div>
            </div>
        </div>
    </div>

        <!--ABOUT SECTION-->>
    <div class="about">
        <AboutMe />    
    </div>

    <!--ABOUT Trailhead-->>
        <div>
            <TrailHead />
        </div>

    <!--ABOUT Certifications-->>
        <div>
            <Certifications />
        </div>

        <!--ABOUT WORK EXPERIENCE-->>
        <div>
            <WorkExperience />
        </div>
</template>

<script>
import Nav from "@/components/Nav.vue";
import AboutMe from "@/components/AboutMe";
import TrailHead from "@/components/TrailHead.vue";
import Certifications from "@/components/Certifications.vue";
import WorkExperience from "@/components/WorkExperience.vue";
export default {
  components: { Nav, AboutMe, TrailHead, Certifications, WorkExperience}
}
</script>

<style lang="scss" scoped>
/*.landing{
display: flex;
/*justify-content: center;*/
/*margin: 0;
padding: 0;*/
/*position: relative;*/
/*width: 100vw;*/
/*left: 50%;
  right: 50%;
  margin-left: -50vw;
  margin-right: -50vw;
}*/

.greet {
    color: #fff;
    text-align: center;
    margin-top: 5rem;
    animation: in 2s ease-in;
    font-family: 'Nunito Sans', sans-serif;
    flex: 3;
}

.salesforceLogo1, .trailheadLogo1{
    width: 6rem;
}

.hi {
    font-size: 4rem;
}

span{
    font-size: 3.5rem;
}

/* .who {
    font-size: 5rem;
    color: aqua;
} */

.wel {
    /*display: inline;*/
    background-color: #0A1128;
    overflow: hidden;
    /*padding-top: 2rem;*/
    /*justify-content: center;*/
    font-family: "Nunito Sans", sans-serif;
    /*text-align: center;*/
    display: flex;
        justify-content: center;
        align-items: center;
        padding-left: 10rem;
                padding-right: 10rem;
}

.image {
    animation: come 2s ease-in;
    display: flex;
    flex: 2;
    align-items: center;
    /*margin-right: 15%; */
}

img {
    width: 24rem;
}

@media (width < 766px) {
    .greet {
        margin-left: auto;
        margin-right: auto;
        margin-top: 1rem;
        font-size: 1.5rem;
        text-align: center;
        padding: 1rem 0rem;
    }

    .hi {
        font-size:1.5rem;
    }

    span{
        font-size: 1.8rem;
    }

    .image {
        display: flex;
        align-items: center;
        margin: 0;
        margin-left: auto;
        margin-right: auto;
    }

    img{
        width: 12rem;
    }

    .who {
        font-size: 2rem;
    }

    .wel {
        display: flex;
        flex-direction: column-reverse;
    }
}

@media (width > 767px) {
    .greet {
        /*margin-left: auto;
        margin-right: auto;
        font-size: 1.7rem;*/
        padding: 1rem 0rem;
        display: flex;
        flex: 3;
        flex-direction: column;
        justify-content: center;
        margin-top: 0rem;
        margin-right: 5rem;
    }

    /*.hi {
        font-size: 1.7rem;
    }*/

    .who {
        font-size: 2.2rem;
    }

    h1 {
        font-size: 1.2rem;
    }

    span{
        font-size: 1.5rem ;
    }

    .image {
        display: flex;
        flex: 2;
        align-items: center;
        margin-top: 1rem;
        justify-content: center;
        /*margin-right: 5%;*/
    }

    img{
        /*width: 18rem;*/
    }

    .wel {
       display: flex;
       flex: 3;
        /*justify-content: space-around;*/
    }

    .h3{
        font-size: 30px;
    }
}
@media (width > 1010px) {
   /* .landing{
display: flex;
/*display: grid;

justify-content: center;
margin: 0;
padding: 0;
position: relative;
width: 100vw;
left: 50%;
  right: 50%;
  margin-left: -50vw;
  margin-right: -50vw;
}*/

    .greet {
       /* margin-left: 15%;*/
        font-size: 1.7rem;
        padding: 1rem 0rem;
            flex: 3;

    }

    /*.hi {
        font-size: 2.5rem;
    }*/

    .who {
        font-size: 4rem;
    }

    /*h3 {
        font-size: 2.5rem;
    }*/

    .image {
        display: flex;
        flex: 2;
        align-items: center;
        margin-top: 1rem;
       /* margin-right: 15%;*/
           flex: 1;

    }

    img{
        /*width: 24rem;*/
    }

    span{
        font-size: 3rem;
    }

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