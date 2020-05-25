<template>
  <v-container fluid grid-list-xl>
    <v-layout row wrap>
      <!-- Widgets-->
      <v-flex d-flex lg3 sm6 xs12>
        <widget
          icon="domain"
          title=" 6 man"
          subTitle="Today's Visits"
          supTitle="see details"
          color="#00b297"
        />
      </v-flex>
      <v-flex d-flex lg3 sm6 xs12>
        <widget
          icon="watch_later"
          title="3 man"
          subTitle="People who are currently using"
          supTitle="see details"
          color="#dc3545"
        />
      </v-flex>
      <v-flex d-flex lg3 sm6 xs12>
        <widget
          icon="computer"
          title="20.12 hr/day"
          subTitle="Operating time "
          supTitle="Summary"
          color="#0866C6"
        />
      </v-flex>
      
      <!-- Widgets Ends -->
      <!-- DataTable&TimeLine Starts -->
      <v-flex d-flex lg8 sm6 xs12>
        <data-table />
      </v-flex>
      <v-flex d-flex lg4 sm6 xs12>
        <!-- <time-line /> -->
      </v-flex>
      <!-- DataTable&TimeLine Ends -->
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      lorem: `Lorem ipsum dolor sit amet, mel at clita quando.`
    };
  }
};
</script>

<style>
.group {
  display: flex;
  flex: 1;
  justify-content: space-around;
}
</style>
