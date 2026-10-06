<template>
    <div>
<div class="abt">
    <div class="about">
      <img src="https://i.postimg.cc/BQDYRcGf/C11-Sibabalwe-Mafestire-3-removebg-preview-1.png
        " alt="">
      <div class="details">
        <h2>Hellozz, I am <span style="color: aqua;">Sibabalwe Mafestire</span></h2>
        <h2 style="font-weight: 600;">Web Developer & Certified Salesforce Professional</h2>
        <p id="info">
          I’m a passionate and multi-skilled Full Stack Developer and Certified Salesforce Professional, driven by a
          love for problem-solving and creating powerful digital solutions. My journey began at Life Choices, where I
          discovered my passion for coding and quickly realized that tech was my true calling. Since then, I’ve
          developed both the technical skills and professional mindset to thrive in fast-paced environments.
          I specialize in web development and have expanded my
          expertise into the Salesforce ecosystem, where I’ve earned multiple certifications and gained hands-on
          experience in customizing orgs, building Lightning Apps, automating business processes, and managing data
          securely.
        </p>
        <p>I thrive on creating meaningful user experiences - whether through seamless web applications or powerful
          Salesforce solutions that drive business efficiency. Every line of code I write and every solution I build is
          fueled by my belief in lifelong learning, impact, and excellence.</p>

          <button class="aboutButton">Read More</button>

       <!-- <div class="two">
          <div>
            <div class="info1">
              <ul class="list-group list-group-vertical ">
                <li class="list-group-item">Address</li>
                <li class="list-group-item p ">Phone</li>
                <li class="list-group-item p n">Linkedin</li>
                <li class="list-group-item p ">Email</li>
                <li class="list-group-item p ">CV</li>
                <li class="list-group-item p ">Full Stack </li>
              </ul>
            </div>

            <div class="info2">
              <ul class="list-group list-group-vertical">
                <li class="list-group-item p ">SEO </li>
                <li class="list-group-item p ">Salesforce Associate</li>
                <li class="list-group-item p ">Salesforce Administrator</li>
                <li class="list-group-item p ">Platform App Builder </li>

              </ul>
            </div>

           
            </div>

            <div>
            <div class="info3">
              <ul class="list-group sec list-group-vertical-sm">
                <l class="list-group-item">Cape Town</l>
                <l class="list-group-item num call"><a class="L" href="tel:+27624244310"
                    style="color: #fff; text-decoration: none;" target="_blank" rel="noopener noreferrer">062 4244 310</a></l>
                <l class="list-group-item num"> <a class="L"
                    href="https://www.linkedin.com/in/sibabalwe-mafestire-804364147"
                    style="color: #fff; text-decoration: none;" target="_blank" rel="noopener noreferrer">Sibabalwe Mafestire</a> </l>
                <l class="list-group-item"><a class="L" href="mailto: seabaraven@gmail.com"
                    style="color: #fff; text-decoration: none;" target="_blank" rel="noopener noreferrer">seabaraven@gail.com</a></l>
                <l class="list-group-item"><a class="L"
                    href="https://i.postimg.cc/J72spk9c/Black-White-Minimalist-CV-Resume-7.png"
                    style="color: #fff; text-decoration: none;" target="_blank" rel="noopener noreferrer">View CV</a></l>
                <l class="list-group-item"><a class="L" href="https://i.postimg.cc/d1J5NXZX/Full-Stack-Certificate.png"
                    style="color: #fff; text-decoration: none;" target="_blank" rel="noopener noreferrer">View Certificate</a></l>
              </ul>
            </div>

            <div class="info4">
              <ul class="list-group sec list-group-vertical-sm">
                <li class="list-group-item"><a class="L" href="https://i.postimg.cc/KjRrdyG9/SEO-certificate.png"
                    style="color: #fff; text-decoration: none;" target="_blank" rel="noopener noreferrer">View Certificate</a></li>
                <li class="list-group-item"><a class="L"
                    href="https://i.postimg.cc/mrpjLSdp/Cert3850456-Associate20231124.png"
                    style="color: #fff; text-decoration: none;" target="_blank" rel="noopener noreferrer">View Certificate</a></li>
                    <li class="list-group-item"><a class="L"
                    href="https://i.postimg.cc/Hj1H69Fp/Cert4661502-Administrator-20240709.png"
                    style="color: #fff; text-decoration: none;" target="_blank" rel="noopener noreferrer">View Certificate</a></li>
                    <li class="list-group-item"><a class="L"
                    href="https://i.postimg.cc/sgZ7Qj47/Cert6199047-Platform-App-Builder-20250522.png"
                    style="color: #fff; text-decoration: none;" target="_blank" rel="noopener noreferrer">View Certificate</a></li>
              </ul>
            </div>
            </div>
        </div>-->
      </div>
    </div>
    

  </div>

    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>

.about {
  padding: 2rem 15rem;
  display: flex;
  flex-direction: row-reverse;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 3rem;
  overflow: hidden;
}

.about img {
  /*width: 25%;*/
  animation: image 2s ease-in;
  align-items: start;
}

.details {
  /*width: 50%;*/
  /*margin-left: auto;
  margin-right: auto;*/
  margin-top: 2rem;
  margin-bottom: 1rem;
  color: white;
  font-family: 'Playfair Display', serif;

}

.two {
  margin-top: 2%;
  width: 90%;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}

.list-group-item p {
  width: 100%;
  margin-right: 5%;
}

.L:hover {
  color: white !important;
}

.details p {
  font-size: 1.1rem;
  margin-left: auto;
  margin-right: auto;
  font-family: 'Nunito Sans', sans-serif;
}

.list-group-item {}

.call {
  width: 110%;
}

.abt {
  /*padding: 2rem 11.1rem;
  margin-bottomm: 6rem;*/

}

.details h2 {
  font-size: 2rem;
  font-family: 'Nunito Sans', sans-serif;
}


.list-group li,
l {
  background-color: #0A1128;
  border: none;
  color: white;
  padding: 0;
  font-family: 'Nunito Sans', sans-serif;
  font-size: 1.1rem;
}

.L{
      color: aqua !important;
}

.aboutButton{
    color: #00A1E0;
      background-color: #0A1128;
    border: 0;
    font-size: 1.3rem;
      font-family: 'Nunito Sans', sans-serif;
      font-weight: 600;
      padding: 0;
}

.aboutButton:hover{
    color: white;

}

/**  --- animation --- */

@keyframes image {
  0% {
    transform: translateY(110%);
  }
}

/** --- responsiveness --- */

@media (width > 900px) {
  .details h2 {
    font-size: 1.6rem;
    border-bottom: none;
    margin-left: 0;
    margin-right: auto;
  }
  
  .details p {
    font-size: 1.1rem;
  }


  .abt {
    margin-left: auto;
    margin-right: auto;
    padding: 1rem 0rem;
  }

  .about img {
    /*text-align: end;
    margin-left: auto;*/
  }

}

@media (width < 900px) {

  .num {
    margin-top: 0;
  }

  .abt {
    margin-top: 0rem;
    margin-left: auto;
    margin-right: auto;
    padding: 1rem 0rem;
  }

  .L {
    width: 80%;
    padding-right: 0;
    color: aqua !important;
  }

  .about {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 0% 8%;
    /* margin-top: 15%; */
  }

  .details {
    width: 100%;
    margin-top: 2rem;
  }

  .about img {
    display: none;
  }

  .details p,
  h2 {
    font-size: 1rem;
  }

  .p {
    margin-top: 0rem;
  }

  .sec {
    padding-left: 3%;
  }


}
</style>