<template>
    <div class="title">Work Experience</div>
    <div class="work">
        <div class="lifechoices">
            <div class="company">
                <img src="https://i.postimg.cc/Hxmk0V1h/Logo-Life-Choices-removebg-preview-(1)-1.png" alt="">
                <div class="date">
                    <p style="color: #00A1E0;">LifeChoices Academy</p>
                    <p>May 2025 - Present</p>
                    <p>Salesforce Technical Lead</p>
                </div>
            </div>
            <div class="roleDescription">
                <p>I am a dedicated and certified Salesforce professional with a strong passion for empowering others through education. With two Salesforce certifications under my belt, I am currently facilitating a Salesforce learning program, where I guide aspiring professionals on their journey to mastering the platform.</p>
                <button class="roleDetails">View More</button>
            </div>
        </div>
        <div class="cirrico">
            <div class="company">
                <img src="https://i.postimg.cc/MTzzMN14/Cirico-logo-removebg-preview-(1)-1.png" alt="">
                <div class="date">
                                        <p style="color: #00A1E0;">Cirrico</p>
                    <p>Nov. 2024 - Jan. 2025</p>
                    <p>Salesforce Associate</p>
                </div>
                </div>
                <div class="roleDescription" >
                    <p style="margin-bottom: 0;">I am a dedicated and certified Salesforce professional with a strong passion for empowering others through education. With two Salesforce certifications under my belt, I am currently facilitating a Salesforce learning program, where I guide aspiring professionals on their journey to mastering the platform.</p>
                </div>
            
        </div>
        <div class="lcStudio">
            <div class="company">
                <img src="https://i.postimg.cc/8CmSS4xj/lc-studioza-logo-removebg-preview.png" alt="" class="studioLogo">
                <div class="date">
                                        <p style="color: #00A1E0;">LC Studio</p>

                    <p>April 2024 - Oct. 2024</p>
                    <p>Dev. Trainee</p>
                </div>
                </div>
                <div class="roleDescription">
                    <p>I am a dedicated and certified Salesforce professional with a strong passion for empowering others through education. With two Salesforce certifications under my belt, I am currently facilitating a Salesforce learning program, where I guide aspiring professionals on their journey to mastering the platform.</p>
                    <button class="roleDetails">View More</button>
                </div>
            
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

.work{
    padding-left: 11rem;
  padding-right: 11rem;
  padding-bottom: 2rem;
  /*display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2rem;*/
  align-items: baseline;
  color: white;
  font-family: 'Nunito Sans', sans-serif;
}

.lifechoices, .cirrico, .lcStudio{
    display: flex;
    justify-content: space-between;
          margin-bottom: 2rem;
          align-items: center;

}

.company {
    flex: 1;
}

.company p{
    margin-bottom: 0;
}

.roleDescription{
    flex: 2;
}

.studioLogo{
    width: 30%;
}

.roleDescription{
    border-left: 3px solid #00A1E0;
    padding-left: 20px;
}
</style>