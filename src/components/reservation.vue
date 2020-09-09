<template>
  <div>
    <div id="headerReservation">
      <h2>Make a reservation!</h2>
    </div>
    <div id="imageReservation">
      <img src="/src/images/reservation-image.png" />
    </div>
    <div id="descriptionAndImage">
      <div id="description">
        <p>
          Our food menu is based on international products combined with local
          flavors. Choose from our list of dishes that contain Breakfast,
          Appetizers, Salads, Fish and Seafood, Pasta, Risotto, Meat, Soups,
          Garnishes and Dessert.
        </p>
        <p>
          Welcoming, CRAFT Pub has over 100sqm, so there is room for everyone.
          We can serve 90 people indoors, 60 people on the outdoor terrace and
          80 people on the Rooftop. If you are a group that wants to eat or just
          drink something cold, CRAFT is exactly what you are looking for.
        </p>
      </div>
      <div id="imageDescription">
        <img src="/src/images/dish-image.jpg" />
      </div>
    </div>
    <div id="formReservation">
      <form id="form1">
        <label>First name: </label>
        <input
          type="text"
          v-model="reservation.firstname"
          placeholder="Ex: Pablo"
          required
        />
        <label>Last name: </label>
        <input
          type="text"
          v-model="reservation.lastname"
          placeholder="Ex: Verani"
          required
        />
        <label>Phone: </label>
        <input
          type="text"
          v-model="reservation.phone"
          placeholder="Ex: 0764253487"
          required
        />
        <label>Table number: </label>
        <input
          type="text"
          v-model="reservation.table"
          v-on:keyup="checkTable"
          placeholder="Ex: 1-7"
          required
        />
        <label>Date: </label>
        <input
          type="text"
          v-model="reservation.date"
          placeholder="Ex: October 21 2020 20:00"
          v-on:keyup="checkDate"
          required
        />
        <input type="button" v-on:click="makeReservation" value="Make it" />
      </form>
    </div>
    <h2 style="color:#6b7b65;text-align:center;">
      {{ result }}. {{tableResult}}
    </h2>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      reservation: {
        firstname: "",
        lastname: "",
        date: "",
        phone: "",
        table: ""
      },
      result: "",
      tableResult:"",
      reservations: {}
    };
  },
  methods: {
    checkTable: function() {
      if (this.reservation.table < 1 || this.reservation.table > 7)
        this.tableResult = "The table number is incorect";
      else this.tableResult = "";
      this.checkDate();

    },
    checkDate: function() {
      //convert dates into numbers
      var date = Date.parse(this.reservation.date);
      var actualHour = new Date();
      var actualHourMiliseconds = Date.parse(actualHour);
      var counter = 0;
      var reservationAlreadyDone = 0;
      //Check if is busy at the date wanted and an hour plus
      for (let i in this.reservations) {
        reservationAlreadyDone = Date.parse(this.reservations[i].date);
        for (let j = 0; j <= 60; j++) {
          if (reservationAlreadyDone == date && this.reservations[i].table == this.reservation.table) counter++;
          reservationAlreadyDone = reservationAlreadyDone + 60000;
        }
      }
      //Asigned a value to result
      if (isNaN(date)) this.result = "Insert date";
      else if (date < actualHourMiliseconds)
        this.result = "This date is already passed";
      else if (date > actualHourMiliseconds && counter > 0)
        this.result = "At that time is busy";
      else if (date > actualHourMiliseconds && counter == 0)
        this.result = "The date is good";
    },
    makeReservation: function() {
      this.$http
        .post(
          "https://vue-restaurant-f7a4e.firebaseio.com/posts.json",
          this.reservation
        )
        .then(function(data) {
          console.log(data);
          this.result = "The reservation was made. Thank you!";
        });
    }
  },
  created() {
    this.$http
      .get("https://vue-restaurant-f7a4e.firebaseio.com/posts.json")
      .then(function(data) {
        return data.json();
      })
      .then(function(data) {
        var reservationArray = [];
        for (let key in data) {
          data[key].id = key;
          reservationArray.push(data[key]);
        }
        this.reservations = reservationArray;
      });
  }
};
</script>

<style scoped>
#headerReservation {
  width: 100%;
  height: auto;
  font-size: 30px;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  text-align: center;
  color: #6b7b65;
}
#imageReservation {
  width: 70%;
  height: auto;
  margin: 0 auto;
  margin-top: 20px;
}
#imageReservation img {
  width: 100%;
  height: auto;
  display: block;
  margin-left: auto;
  margin-right: auto;
}
#descriptionAndImage {
  display: flex;
  flex-direction: row;
  width: 85%;
  height: auto;
  margin: 0 auto;
  margin-top: 80px;
  align-items: center;
}
#description {
  width: 50%;
  height: auto;
  background-color: white;
  box-shadow: -1px 1px 12px 1px #888888;
  font-family: Bradley Hand, cursive;
  font-size: 20px;
  word-wrap: break-word;
}
#imageDescription {
  width: 50%;
  height: auto;
  border: 2px solid black;
}
#imageDescription img {
  width: 100%;
  height: auto;
  display: block;
}
#formReservation {
  width: 40%;
  height: auto;
  margin: 0 auto;
  margin-top: 70px;
  text-align: center;
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}
input[type="text"],
select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

input[type="button"] {
  width: 100%;
  background-color: #6b7b65;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
label {
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
}
</style>
