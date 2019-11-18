<template>
  <div class="counter">
    <div class="counter__time days">{{values.days}}</div>
    <div class="counter__time hours">{{values.hours}}</div>
    <div class="counter__time minutes">{{values.minutes}}</div>
    <div class="counter__time seconds">{{values.seconds}}</div>
    <div class="destination-time">
      <h1 class="destination-time__title">Data</h1>
      <input
        id="time-input"
        type="datetime-local"
        value="2019-12-15T20:00:00"
        min-value="2000-01-01T00:00"
        max-value="2099-12-31T23:59"
        class="destination-time__input"
        v-model="title"
      />
      <div class="destination-time__error"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Counter",
  data() {
    return {
      title: "2019-12-15T20:00",
      values: {
        days: "",
        hours: "",
        minutes: "",
        seconds: ""
      }
    };
  },
  methods: {
    value: function() {},
    calcValue: function() {
      let self = this;
      setInterval(function() {
        let currentDate = new Date(self.title).getTime();
        let end = currentDate;
        let start = new Date().getTime();
        let value = end - start;
        self.values = {
          days: Math.floor(value / 86400000),
          hours: Math.floor(
            (value - Math.floor(value / 86400000) * 86400000) / 3600000
          ),
          minutes: Math.floor(
            (value -
              Math.floor(value / 86400000) * 86400000 -
              Math.floor(
                (value - Math.floor(value / 86400000) * 86400000) / 3600000
              ) *
                3600000) /
              60000
          ),
          seconds: Math.floor(
            (value -
              Math.floor(value / 86400000) * 86400000 -
              Math.floor(
                (value - Math.floor(value / 86400000) * 86400000) / 3600000
              ) *
                3600000 -
              Math.floor(
                (value -
                  Math.floor(value / 86400000) * 86400000 -
                  Math.floor(
                    (value - Math.floor(value / 86400000) * 86400000) / 3600000
                  ) *
                    3600000) /
                  60000
              ) *
                60000) /
              1000
          )
        };
      }, 1000);
    }
  }
};
</script>



<style scoped>
.counter {
  padding: 10vh 50px;
}
.counter__time {
  display: inline-block;
  min-width: 80px;
  min-height: 50px;
  padding: 20px 5px;
  border-radius: 10px;
  border: dotted red 5px;
  font-size: 2.2em;
  font-weight: bold;
  margin: 10px;
  text-align: center;
  line-height: 1em;
  background-color: rgba(255, 0, 0, 0.4);
  -webkit-transition: 2s;
  transition: 2s;
}
.destination-time {
  margin-top: 15vh;
}

.destination-time__title {
  font-size: 24px;
}

.destination-time__input {
  margin-top: 2vh;
  font-size: 16px;
  font-weight: bold;
  min-width: 200px;
  background-color: rgba(0, 0, 0, 0.05);
  color: white;
  border: 0;
}
.destination-time__error {
  color: red;
  font-size: 1.1em;
  font-weight: bold;
  margin-top: 0.1em;
}
</style>