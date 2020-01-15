<template>
  <div>
    <h1>Days until birthday</h1>
    <br />

    Days until Birthday: <br /><br />
    <!-- <span style="color:red;">{{ daysUntilBirthday }}</span> days.. -->
    Kotryna -
    <span style="color:red;">{{ daysUntilBirthday1("1999-04-15") }}</span> days
    <br />
    Mindaugas - {{ daysUntilBirthday1("1979-04-21") }} days <br />
    Arminas - {{ daysUntilBirthday1("1979-04-22") }} days <br />
    Zita - {{ daysUntilBirthday1("1982-05-09") }} days <br />
    Uma - {{ daysUntilBirthday1("2012-07-09") }} days <br />
    Ilajus - {{ daysUntilBirthday1("2014-12-17") }} days <br />
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
      ],
      today: moment().format("YYYY-MM-DD")
      //   birthday: moment("2014-11-14").format("YYYY-MM-DD")
    };
  },
  //   computed: {
  //     birthday: function() {
  //       //return  moment(this.person.birthdayb).format('YYYY-MM-DD')
  //       return moment(this.person.birthday).format("YYYY-MM-DD");
  //     },
  //     //Calculate current age of person in years (moment truncates by default)
  //     years: function() {
  //       return moment().diff(this.birthday, "years");
  //     },
  //     liveddays: function() {
  //       return moment().diff(this.birthday, "days");
  //     },
  //     daysUntilBirthday: function() {
  //       let today = moment().format("YYYY-MM-DD");
  //       let adjustToday =
  //         this.birthday.substring(5) === today.substring(5) ? 0 : 1;
  //       let nextBirthday = moment(this.birthday).add(
  //         this.years + adjustToday,
  //         "years"
  //       );
  //       return nextBirthday.diff(this.today, "days");
  //     }
  //   },
  methods: {
    // birthday: function() {
    //return  moment(this.person.birthdayb).format('YYYY-MM-DD')
    //   return moment(this.person.birthday).format("YYYY-MM-DD");
    // },
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
      //   var today = moment().format("YYYY-MM-DD");
      var adjustToday =
        birthday.substring(5) === this.today.substring(5) ? 0 : 1;
      var nextBirthday = moment(birthday).add(years + adjustToday, "years");
      return nextBirthday.diff(this.today, "days");
      //   return adjustToday;
    }
  }
};
</script>

<style></style>
