<template>
  <div id="body-home">
    <div id="restaurantView">
      <i class="fa fa-chevron-left" v-on:click="imageChangeLeft"></i>
      <div id="photosChange">
        <img src="/src/images/restaurantView.jpg" class="imgs" />
        <img src="/src/images/restaurant1.jpg" class="imgs" />
        <img src="/src/images/restaurant2.jpg" class="imgs" />
      </div>
      <i class="fa fa-chevron-right" v-on:click="imageChangeRight"></i>
    </div>
    <div id="home-content">
      <div class="home-info">
        <p><span>Craft</span></p>
        <p>
          It is located on the Napoli coast, very close to the sea and the most
          important attractions of the city. It soon became the favorite place
          of locals and tourists visiting Napoli. You can choose from our list
          of dishes that contain Breakfast, Appetizers, Salads, Fish and
          Seafood, Pasta, Risotto, Meat, Soups, Garnishes and Dessert or a
          special wine.
        </p>
      </div>
      <div class="content-image">
        <img src="/src/images/contentImage.jpg" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      position: 0,
      speed: 63
    };
  },
  methods: {
    imageChangeLeft: function() {
      if(this.position < 0 ){
      this.position = this.position + this.speed;
      var image = document.getElementsByClassName("imgs");
      image[0].style.marginLeft = this.position + "vw";
    }
    },
    imageChangeRight: function() {
      if(this.position > this.speed * -2){
      this.position = this.position - this.speed;
      var image = document.getElementsByClassName("imgs");
      image[0].style.marginLeft = this.position + "vw";
    }
    }
  },
  created() {}
};
</script>

<style scoped>
#body-home{
  animation: toTheRight 1.25s linear;
}
#restaurantView {
  width: 70vw;
  height: auto;
  margin: 0 auto;
  margin-top: 5px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-evenly;
}
#photosChange {
  display: flex;
  flex-direction: row;
  width: 90%;
  height: auto;
  overflow: hidden;
}
#photosChange img {
  display: block;
  width: 100%;
  height: auto;
  transition: 1s;
}
#photosChange img:first-of-type {
  display: block;
}
i {
  font-size: 40px;
  color: #6b7b65;
  z-index: 3;
}
#home-content {
  display: flex;
  flex-direction: row;
  width: 85%;
  height: auto;
  margin: 0 auto;
  margin-top: 70px;
  margin-bottom: 70px;
  align-items: center;
}
.home-info {
  width: 50%;
  height: auto;
  background-color: white;
  box-shadow: -1px 1px 12px 1px #888888;
  font-family: Bradley Hand, cursive;
  font-size: 20px;
  word-wrap: break-word;
}
.home-info p {
  padding: 25px 20px 20px;
}
.home-info span {
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  font-size: 30px;
  color: #61985c;
  border-bottom: 3px solid gray;
  text-indent: 15px;
}
.content-image {
  width: 50%;
  height: auto;
  border: 2px solid black;
}
.content-image img {
  width: 100%;
  height: auto;
  display: block;
}
@keyframes toTheRight{
  from{transform:translateX(-120%);
        opacity: 0.5;}
  to{transform:translateX(0%);
    opacity: 1;}
}
</style>
