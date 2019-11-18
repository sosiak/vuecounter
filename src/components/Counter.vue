<template>
  <div class="counter">
    <div class="counter__time days">{{convertValue().days}}</div>
    <div class="counter__time hours">{{convertValue().hours}}</div>
    <div class="counter__time minutes">{{convertValue().minutes}}</div>
    <div class="counter__time seconds">{{convertValue().seconds}}</div>
    <div class="destination-time">
      <h1 class="destination-time__title">Data</h1>
      <input
        id="time-input"
        type="datetime-local"
        value="2019-12-15T20:00:00"
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
      title: "2019-12-15T20:00"
    };
  },
  methods: {
    value: function inputValue() {
      return new Date(this.title).getTime();
    },
    calcValue: function calculateToListItem() {
      const end = this.value();
      const start = new Date().getTime();
      return end - start;
    },
    convertValue: function convertToTimeValues() {
      let value = this.calcValue();
      let values = {
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
      return values;
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