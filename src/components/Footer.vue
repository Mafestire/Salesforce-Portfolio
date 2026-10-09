<template>
    <div class="footer">
        <p>&copy;2023 Sibabalwe Mafestire</p>

        <div class="foot">
            
<!--             <div class="quick">
                <h5>Quick links</h5>
                <ul class="links">
                    <li><router-link to="/about">About</router-link></li>
                    <li><router-link to="/#skills">Resume</router-link></li>
                    <li><router-link to="/projects#Projects">Projects</router-link></li>
                    <li><router-link to="/projects#Testimonials">Testimonials</router-link></li>
                </ul>
            </div> -->

            <div class="connect">
                <h5>Socials</h5>

                <ul class="socials">
                    <li><a href="https://www.linkedin.com/in/sibabalwe-mafestire-804364147" target="_blank" rel="noopener noreferrer">LinkedIn</a></li>
                    <li><a href="https://github.com/Mafestire">Git</a></li>
                    <li><a href="https://www.salesforce.com/trailblazer/profile/sibabalwemafestire" target="_blank" rel="noopener noreferrer">Trail Head</a></li>
                    <li><a href="mailto: seabaraven@gmail.com" target="_blank" rel="noopener noreferrer">Email</a></li>
                </ul>
            </div>

        </div>

    </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.footer {
    display: flex;
    flex-direction: column-reverse;
    justify-content: space-between;
    align-items: center;
    font-family: 'Nunito Sans', sans-serif;
    padding-top: 1rem;
    /* margin-top: 4rem; */
}

.footer p {
    font-size: 1rem;
    color: #00A1E0;
    width: 100%;
    text-align: center;
    /* padding-top: 1rem; */
}

.foot {
    width: 100%;
    padding-bottom: 1rem;
        padding-top: 2%;
        border-top: 1px solid #000;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
}

.links {
    display: flex;
    flex-direction: row;
}

.links li,
.socials li {
    list-style: none;
    font-size: 1rem;
}

li a {
    list-style: none;
    text-decoration: none;
    margin-right: 15px;
    font-size: 20px;
    color: #fff;
}

li a:hover {
    color: #00A1E0;
}

.socials {
    color: #fff;
    font-size: 20px;
    display: flex;
    flex-direction: row;
}

h5{
    color: #00A1E0;
    padding-left: 2rem;
    font-size: 1.5rem;
}
</style>