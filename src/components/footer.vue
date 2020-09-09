<template>
  <div id="myFooter">
    <div id="footer-1">
      <div class="program">
        <p><span>Program</span></p>
        <p>Monday <span> 10 AM - 10 PM</span></p>
        <p>Tuesday <span> 10 AM - 10 PM</span></p>
        <p>Wednesday <span> 10 AM - 10 PM</span></p>
        <p>Thursday <span> 10 AM - 10 PM</span></p>
        <p>Friday <span> 10 AM - 10 PM</span></p>
        <p>Saturday <span> 10 AM - 12 PM</span></p>
        <p>Sunday <span> 10 AM - 12 PM</span></p>
      </div>
      <div class="tripadvisor">
        <p><span>Tripadvisor</span></p>
        <div class="imgtrip">
          <img src="/src/images/tripadvisor.png" />
        </div>
      </div>
    </div>
    <div id="footer-2">
      <div class="social">
        <div class="icon"><i class="fa fa-facebook"></i></div>
        <div class="icon"><i class="fa fa-instagram"></i></div>
        <div class="icon"><i class="fa fa-snapchat"></i></div>
      </div>
      <div class="policy">
          <p>Privacy policy</p>
          <p>Terms and conditions</p>
          <p>Cookie policy</p>
          <p>Copyright @ 2020 Craft Restaurant Napoli. All rights reserved.</p>
      </div>
      
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {};
  }
};
</script>

<style scoped>
#myFooter{
  animation: toTheLeft 1.25s linear;
}
#footer-1 {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-evenly;
  width: 100%;
  height: auto;
  background-color: #424242;
}
.program {
  width: 30%;
  height: auto;
  margin-bottom: 30px;
}
.tripadvisor {
  width: 30%;
  height: auto;
  margin-bottom: 30px;
}
.imgtrip {
  width: 100%;
  height: auto;
}
.imgtrip img {
  display: block;
  width: 40%;
  height: auto;
  margin-left: auto;
  margin-right: auto;
}
.program p {
  color: #d4d4d4;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
.program p:first-child {
  border-bottom: 2px solid gray;
  text-align: center;
  font-size: 25px;
}
.program p + p {
  border-bottom: 1px dotted gray;
}
.program span + span {
  text-align: right;
}
.tripadvisor p {
  color: #d4d4d4;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
.tripadvisor p:first-child {
  border-bottom: 2px solid gray;
  text-align: center;
  font-size: 25px;
}
#footer-2 {
  width: 100%;
  height: auto;
  background-color: #343434;
}
.social {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-evenly;
  width: 15%;
  height: auto;
  margin: 0 auto;
}
.icon {
  width: 12%;
  margin-top: 70px;
}
i {
  font-size: 2rem;
  color: #d4d4d4;
}
.policy{
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-evenly;
  width: 40%;
  height: auto;
  margin: 0 auto;
  margin-top:30px ;
}
.policy p{
      font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
      font-size: 23px;
      color: #d4d4d4;
      border-bottom: 2px solid gray;
}
@keyframes toTheLeft{
  from{transform:translateX(120%);
        opacity: 0.5;}
  to{transform:translateX(0%);
    opacity: 1;}
}
</style>
