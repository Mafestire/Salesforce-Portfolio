<template>
    <div class="title">Certifications</div>
    <div class="Certification">
        <div class="associate">
            <img src="https://i.postimg.cc/TP9SBgxF/Associate-badge-1.png" alt="">
            <p>Salesforce <br> Associate</p>
        </div>
        <div class="admin">
            <img src="https://i.postimg.cc/9QHnMJQ5/administrator-badge-1.png" alt="">
            <p>Salesforce <br> Platform Administrator</p>
        </div>
        <div class="appBuilder">
            <img src="https://i.postimg.cc/Pq23SHzT/App-Builder-Logo-removebg-preview-1.png" alt="">
            <p>Salesforce <br> Platform App Builder</p>
        </div>
        <div class="agentforce">
            <img src="https://i.postimg.cc/T1Wt2D81/Agentforce-Specialist-Logo-removebg-preview-1.png" alt="">
            <p>Salesforce <br> Agentforce Specialist</p>
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

.Certification{
    padding-left: 11rem;
  padding-right: 11rem;
  padding-bottom: 2rem;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2rem;
  align-items: baseline;
  color: white;
  font-family: 'Nunito Sans', sans-serif;
}

.associate, .admin, .appBuilder, .agentforce {
    display: flex;
    font-size: 24px;
      align-items: center;
}

.associate img, .admin img, .appBuilder img, .agentforce img{
    padding-right: 3rem;
}
</style>