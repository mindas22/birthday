<template>
  <div>
    <div class="container">
      <h1>Days until birthday</h1>
      <div class="list">
        Kotryna - {{ daysUntilBirthday("1999-04-15") }} days
        <br />
        Mindaugas - {{ daysUntilBirthday("1979-04-21") }} days <br />
        Arminas - {{ daysUntilBirthday("1979-04-22") }} days <br />
        Algis - {{ daysUntilBirthday("1944-04-26") }} days <br />
        Zita - {{ daysUntilBirthday("1982-05-09") }} days <br />
        Uma - {{ daysUntilBirthday("2012-07-09") }} days <br />
        Laimute - {{ daysUntilBirthday("1958-07-18") }} days <br />
        Ilajus - {{ daysUntilBirthday("2014-12-17") }} days <br />
      </div>
      <bcalc bdate="2008-04-22" name="Arminas" />
      <bcalc bdate="1944-04-26" name="Algis" />
      <bcalc bdate="2014-12-17" name="Ilajus" />
      <bcalc bdate="2000-01-01" name="JOE" />
    </div>
  </div>
</template>

<script>
import moment from "moment";
import bcalc from "@/components/bcalc.vue";

export default {
  data() {
    return {
      today: moment().format("YYYY-MM-DD")
    };
  },
  components: {
    bcalc
  },
  methods: {
    //Calculate current age of person in years (moment truncates by default)
    // years: function() {
    //   return moment().diff(this.birthday, "years");
    // },
    // liveddays: function() {
    //   return moment().diff(this.birthday, "days");
    // },
    daysUntilBirthday: function(val) {
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
