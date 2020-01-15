<template>
  <div>
    <h1>Days until birthday</h1>
    <br />
    <div v-for="person in persons" :key="person.name">
      -{{ person.name }} -> {{ person.birthdayb }} -
    </div>
    <br />
    <!-- {{ years }} -->

    Days until Birthday:
    <span style="color:red;">{{ daysUntilBirthday }}</span> days..

    <br />

    Total lived <span class="days">{{ liveddays }}</span> days.
    <br />
  </div>
</template>

<script>
import moment from "moment";

export default {
  data() {
    return {
      birthdays: [],
      person: {
        name: "Julija",
        birthday: "1929-12-12"
      },
      persons: [
        {
          name: "John",
          birthdayb: "2014-12-17"
        },
        {
          name: "Eve",
          birthdayb: "2012-07-09"
        }
      ]
      //   birthday: moment("2014-11-14").format("YYYY-MM-DD")
    };
  },
  computed: {
    birthday: function() {
      //return  moment(this.person.birthdayb).format('YYYY-MM-DD')
      return moment(this.person.birthday).format("YYYY-MM-DD");
    },
    //Calculate current age of person in years (moment truncates by default)
    years: function() {
      return moment().diff(this.birthday, "years");
    },
    liveddays: function() {
      return moment().diff(this.birthday, "days");
    },
    daysUntilBirthday: function() {
      let today = moment().format("YYYY-MM-DD");
      let adjustToday =
        this.birthday.substring(5) === today.substring(5) ? 0 : 1;
      let nextBirthday = moment(this.birthday).add(
        this.years + adjustToday,
        "years"
      );
      return nextBirthday.diff(this.today, "days");
    }
  }
};
</script>

<style></style>
