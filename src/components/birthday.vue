<template>
  <div>
    <div class="container">
      <h1>Days until birthday</h1>
      <div class="list">
        Kotryna -
        <span style="color:red;">{{ daysUntilBirthday1("1999-04-15") }}</span>
        days
        <br />
        Mindaugas - {{ daysUntilBirthday1("1979-04-21") }} days <br />
        Arminas - {{ daysUntilBirthday1("1979-04-22") }} days <br />
        Algis - {{ daysUntilBirthday1("1944-04-26") }} days <br />
        Zita - {{ daysUntilBirthday1("1982-05-09") }} days <br />
        Uma - {{ daysUntilBirthday1("2012-07-09") }} days <br />
        Laimute - {{ daysUntilBirthday1("1958-07-18") }} days <br />
        Ilajus - {{ daysUntilBirthday1("2014-12-17") }} days <br />
      </div>
    </div>
  </div>
</template>

<script>
import moment from "moment";

export default {
  data() {
    return {
      today: moment().format("YYYY-MM-DD")
    };
  },
  methods: {
    //Calculate current age of person in years (moment truncates by default)
    // years: function() {
    //   return moment().diff(this.birthday, "years");
    // },
    // liveddays: function() {
    //   return moment().diff(this.birthday, "days");
    // },
    daysUntilBirthday: function() {
      var birthday = moment().format("YYYY-MM-DD");
      var years = moment().diff(birthday, "years");
      var today = moment().format("YYYY-MM-DD");
      var adjustToday = birthday.substring(5) === today.substring(5) ? 0 : 1;
      var nextBirthday = moment(birthday).add(years + adjustToday, "years");
      return nextBirthday.diff(today, "days");
    },
    daysUntilBirthday1: function(val) {
      var birthday = moment(val).format("YYYY-MM-DD");
      var years = moment().diff(birthday, "years");
      var adjustToday =
        birthday.substring(5) === this.today.substring(5) ? 0 : 1;
      var nextBirthday = moment(birthday).add(years + adjustToday, "years");
      return nextBirthday.diff(this.today, "days");
    }
  }
};
</script>

<style>
.list {
  font-size: 34px;
}
.container {
  height: 100vh;
  border: 1px solid chartreuse;
}
</style>
