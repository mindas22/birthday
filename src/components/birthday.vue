<template>
  <div>
    <div class="container">
      <h1>Days until birthday</h1>
      <div class="list">
        K -
        {{ daysUntilBirthday("1999-04-15") }} days
        <br />
        Min - {{ daysUntilBirthday("1979-04-21") }} days <br />
        Arm - {{ daysUntilBirthday("2008-04-22") }} days <br />
        Z - {{ daysUntilBirthday("1982-05-09") }} days <br />
        U - {{ daysUntilBirthday("2012-07-09") }} days <br />
        Laimute - {{ daysUntilBirthday("1958-07-18") }} days <br />
        Halloween - {{ daysUntilBirthday("2020-10-31") }} days <br />
        I - {{ daysUntilBirthday("2014-12-17") }} days <br />
      </div>
      <bcalc bdate="2010-04-04" name="Maja" />
      <bcalc bdate="1979-04-21" name="Min" />
      <bcalc bdate="2008-04-22" name="A" />
      <bcalc bdate="2012-07-09" name="U" />
      <bcalc bdate="2014-12-17" name="I" />
    </div>
  </div>
</template>

<script>
import moment from "moment";
import bcalc from "@/components/bcalc.vue";

export default {
  data() {
    return {
      today: moment().format("YYYY-MM-DD"),
    };
  },
  components: {
    bcalc,
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
    },
  },
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
