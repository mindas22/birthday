<template>
  <div>
    <p>{{name}} - {{daysUntilBirthday(bdate)}} days until birthday, age: {{years}} years, total lived {{liveddays}} days. {{bdate}} </p>
  </div>
</template>

<script>
import moment from "moment";

export default {
  props: {
    bdate: String,
    name: String
  },
  data() {
    return {
      today: moment().format("YYYY-MM-DD")
    };
  },
  computed: {
    years: function() {
      return moment().diff(this.bdate, "years");
    },
    liveddays: function() {
      return moment().diff(this.bdate, "days");
    }
  },
  methods: {
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

<style></style>
