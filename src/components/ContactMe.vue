<template>
    <div class="title">Work Experience</div>
    <div class="contacts">
        <div class="socials">
            <div class="trailblazer">
                <div class="logo">
                    <img src="https://i.postimg.cc/d3K28C86/Trailhead-Logo-removebg-preview.png" alt="">
                </div>
                <div class="info">
                    <p class="smallTitle">Trailblazer:</p>
                    <p>Sibabalwe Mafestire</p>
                </div>
            </div>
            <div class="linkedIn">
                <div class="logoLinkedIn">
                    <img src="https://i.postimg.cc/Wb8GkhtW/Linkedin-Logo-removebg-preview.png" alt="">
                </div>
                <div class="info">
                    <p class="smallTitle">LinkedIn:</p>
                    <p>Sibabalwe Mafestire</p>
                </div>
            </div>
            <div class="email">
                <div class="logoEmail">
                    <img src="https://i.postimg.cc/x1nG4LNc/Email-Icon-removebg-preview.png" alt="">
                </div>
                <div class="info">
                    <p class="smallTitle">Email:</p>
                    <p>seabaraven@gmail.com</p>
                </div>
            </div>
        </div>

        <div class="contactForm">
            <Form class="form" action="https://formspree.io/f/mjvdvzqd" method="post">
          <!--  <div class="hd">
                <h2>Send me a Message</h2>
                <div class="p"></div>
            </div> -->

           <!-- <label for="Name " class="one">Full Name</label> -->
            <input type="text " class="one-o" name="Name" id="name" placeholder="Enter Name" required>
           <!-- <label for="email " class="two">Email</label> -->
            <input type="email " class="two-o" name="email" id="email" placeholder="Enter Email Address" required>
           <!-- <label for="number" class="three">Contact Number</label> -->
            <input type="number" class="three-o" name="number" id="number" placeholder="Enter Contact Number" required>
            <!-- <label for="message" class="four">Message</label> -->
            <textarea type="text" class="four-o" name="message" id="message" placeholder="Type in message" required></textarea>
            <button type="submit" class="five">Submit</button>
        </Form>
        </div>

    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>
.title{
    padding: 2rem 11rem;
    font-size: 40px;
    font-weight: 900;
    color: #00A1E0;
    font-family: 'Nunito Sans', sans-serif;
}

.contacts{
    padding: 2rem 14rem;
    display: flex;
    justify-content: space-between;
    color: white;
        font-family: 'Nunito Sans', sans-serif;
    font-size: 1.2rem;
}

.socials, .contactForm{
    flex: 1;
}

.logo img{
    width: 60%;
}
.logoEmail img, .logoLinkedIn img{
    width: 55%;
    padding-left: .5rem;
}

.logo, .logoEmail, .logoLinkedIn{
    flex: 1;
        align-items: center;
        justify-content: center;

}

.info{
    flex: 3;
    align-items: center !important;
}

.info p{
    margin-bottom: 0;
}

.trailblazer, .linkedIn, .email{
    display: flex;
        align-items: center !important;
        margin-bottom: 1rem;

}

.smallTitle{
    font-size: 1.5rem;
    font-weight: bolder;
    color: #00A1E0;
}

.form{
    display: flex;
    flex-direction: column;
        border: none;align-items: start;
    width: 100%;
}

input,
textarea {
    font-size: 18px;
    padding-top: 1rem;
    margin-bottom: 1rem;
    width: 100%;
      background-color: transparent;
    color: #fff;
    border: none;
    border-bottom: 2px solid #00A1E0;
    /*text-align: center;*/
}

button {
    /*width: 5rem;*/
    font-size: 18px;
    padding: 0;
    margin-top: 1rem;
    border: none;
    color: #00A1E0;
    font-weight: 600;
    border: 0px solid #00A1E0;
      background-color: transparent;
}

button:hover{
    color: white;
}
</style>