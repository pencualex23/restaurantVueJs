<template>
  <div id="myHeader">
    <div class="adress">
      <p>Street Cavali Ferroni 5, Napoli, Italy</p>
      <p>+400764233742 , pencu_alex701@yahoo.com</p>
    </div>
    <div class="logo">
      <img src="/src/images/logo.png" />
    </div>
    <div class="social">
      <div class="icon"><i class="fa fa-facebook"></i></div>
      <div class="icon"><i class="fa fa-instagram"></i></div>
      <div class="icon"><i class="fa fa-snapchat"></i></div>
    </div>
    <nav>
      <router-link to="/" exact>Home</router-link>
      <a href="#">About Us</a>
      <a href="#">Drinks Menu</a>
      <a href="#">Food Menu</a>
      <router-link to="/reservation" exact>Reservation</router-link>
      <a href="#">Contact</a>
    </nav>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  }
};
</script>

<style scoped>
#myHeader {
  background-color: #424242;
  width: 100%;
  height: auto;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-evenly;
  animation: toTheLeft 1.25s linear;
}
.adress {
  width: 20%;
  color: #d4d4d4;
  text-align: center;
  font-size: 14px;
  margin-left: 10%;
  font-family: Bradley Hand, cursive;
}
.logo {
  width: 40%;
}
.logo img {
  width: 50%;
  height: auto;
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.social {
  width: 20%;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  margin-right: 5%;
}
.icon {
  width: 12%;
}
i {
  font-size: 2rem;
  color: #d4d4d4;
}
nav {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-evenly;
  width: 75%;
  margin: 0 auto;
  margin-top: 25px;
  background-color: #6b7b65;
  align-items: center;
}
nav a {
  text-decoration: none;
  font-size: 20px;
  color: #d4d4d4;
  transition: 2s;
  padding-top: 15px;
  padding-bottom: 15px;
}
a:hover {
  color: white;
}
#restaurantView {
  width: 70%;
  height: auto;
  margin: 0 auto;
}
#restaurantView img {
  display: block;
  width: 100%;
}
@keyframes toTheLeft{
  from{transform:translateX(120%);
        opacity: 0.5;}
  to{transform:translateX(0%);
    opacity: 1;}
}
</style>
