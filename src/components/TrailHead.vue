<template>

    <div class="title">Trailhead</div>

  <div class="trailhead">
        <div class="logo">
            <img
                src="https://i.postimg.cc/s29cNm3q/Trailhead-Logo-removebg-preview.png"
                alt=""
            />
        </div>

        <div class="trailheadPoints">
            <div class="badges">
                <div class="badgeNumber">
                    <p>63</p>
                </div>
                <div class="badge">
                    <p>badges</p>
                </div>
            </div>
            <div class="points">
                <div class="pointNumber">
                    <p>66,125</p>
                </div>
                <div class="point">
                    <p>Points</p>
                </div>
            </div>
            <div class="superbadges">
                <div class="superbadgeNumber">
                    <p>15</p>
                </div>
                <div class="superbadge">
                    <p>Superbadges</p>
                </div>
            </div>
        </div>

         <div class="trailheadLink">
            <div class="trailblazerLink">
                <img
                    src="https://i.postimg.cc/dVcGcCNq/Link-logo-removebg-preview.png"
                    alt=""
                />
            </div>
            <div class="trailblazer">
                <p>Trailblazer  Profile Link</p>
            </div>
        </div>

    </div>
       
</template>

<script setup></script>

<style lang="scss" scoped>

.title{
      padding: 2rem 11rem;
    font-size: 40px;
    font-weight: 900;
    color: #00A1E0;
  font-family: 'Nunito Sans', sans-serif;
}

.trailhead {
  padding: 0rem 13rem;
  padding-bottom: 2rem;
  display: flex;
  flex-direction: row;
  align-items: baseline;
  color: white;
  font-family: 'Nunito Sans', sans-serif;
}

.logo {
  width: 20%;
}

.logo img {
  width: 100%;
}

.trailheadPoints {
    width: 65%;
  display: flex;
  justify-content: space-around;
}

.trailheadPoints p, .badge, .trailblazer p{
    padding: 0;
    margin: 0;
    font-size: 24px;
    font-weight: 900 !important;
  font-family: 'Nunito Sans', sans-serif;
}

.badgeNumber, .pointNumber, .superbadgeNumber {
    color: #00A1E0;
}

.trailheadLink {
  display: flex;
  align-items: baseline;
}

.trailblazerLink img {
  width: 40%;

}

.trailblazerLink {
    flex: 1;
     display: flex;
    justify-content: flex-end;
    /*align-self: center;
    width: 40%;
      align-items: start;*/

}

.trailheadLink {
    align-self: center;
   
/*        align-items: end !important;

width: 30%;
  align-items: end;*/
}

.trailblazer{
    flex: 2;
}
</style>
