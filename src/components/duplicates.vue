<template>
  <v-card>
    <div>
      <v-col class="pa-0">
        <div class="grey lighten-3 pa-3">
          <v-text-field
            v-model="search"
            append-icon="mdi-magnify"
            label="Search by Account/Lead Name"
            solo
            single-line
            hide-details
          ></v-text-field>
        </div>

        <v-row no-gutters class="pa-3 grey--text text--darken-1">
          <v-col cols="5">
            <div class="caption">Showing:</div>
            <div class="font-weight-black">10 out of {{Object.keys(duplicates).length}} duplicates</div>
          </v-col>
          <v-col cols="2">
            <div class="caption">Completion Goal</div>
            <div class="font-weight-black blue--text text--darken-4">
              <v-icon left color="blue darken-4">timer</v-icon>30 minutes
            </div>
          </v-col>
          <v-col cols="2">
            <div class="caption">Time Left</div>
            <div class="font-weight-black orange--text text--darken-3">
              <v-icon left color="orange darken-3">timer</v-icon>12 minutes
            </div>
          </v-col>
          <v-col cols="3" class="text-right">
            <v-btn color="blue darken-4" dark>REVIEW ALL</v-btn>
          </v-col>
        </v-row>
      </v-col>
    </div>
    <v-data-table :headers="headers" :items="duplicates" :search="search">
      <template v-slot:item.required_time="{ item }">
        <div class="orange--text text--darken-3">
          <v-icon left color="orange darken-3">timer</v-icon>
          {{ item.required_time | formatTime }}
        </div>
      </template>
      <template v-slot:item.source="{ item }">
        <div class="font-weight-bold">{{ item.source }}</div>
      </template>
      <template v-slot:item.name="{ item }">
        <div class="blue--text text--darken-4">{{ item.name }}</div>
      </template>
    </v-data-table>
  </v-card>
</template>

<script>
export default {
  filters: {
    formatTime(time) {
      // I use time in seconds so I can ordered it in the table I've could also used a timestamp Unix format
      if (time >= 60) {
        return Number(time) / 60 + " min";
      } else {
        return time + " sec";
      }
    }
  },
  data() {
    return {
      search: "",
      headers: [
        {
          text: "Required time",
          align: "start",
          value: "required_time"
        },
        { text: "Source", value: "source" },
        { text: "Name", value: "name" },
        { text: "Billing Street", value: "billing_street" },
        { text: "Billing City", value: "billing_city" }
      ],
      duplicates: [
        {
          required_time: "20",
          source: "Lead",
          name: "Dream Folks",
          billing_street: "2335 N. Michigan Avenue",
          billing_city: "New York"
        },
        {
          required_time: "20",
          source: "Account",
          name: "Jhonson & Co",
          billing_street: "2335 Michigan Avenue",
          billing_city: "New York"
        },
        {
          required_time: "30",
          source: "Account",
          name: "Microfirst",
          billing_street: "2335 N. Michigan Avenue",
          billing_city: "New Jersey"
        },
        {
          required_time: "30",
          source: "Lead",
          name: "First Alarm",
          billing_street: "2335 N. Michigan Avenue",
          billing_city: "Dallas"
        },
        {
          required_time: "30",
          source: "Lead",
          name: "Dream Folks",
          billing_street: "2335 Michigan Avenue",
          billing_city: "Austin"
        },
        {
          required_time: "30",
          source: "Lead",
          name: "Jhonson & Co",
          billing_street: "2335 N. Michigan Avenue",
          billing_city: "Anew York"
        },
        {
          required_time: "40",
          source: "Lead",
          name: "Dream Folks",
          billing_street: "2335 N. Michigan Avenue",
          billing_city: "Boston"
        },
        {
          required_time: "40",
          source: "Lead",
          name: "Jhonson & Co",
          billing_street: "2335 Michigan Avenue",
          billing_city: "San Franciso"
        },
        {
          required_time: "50",
          source: "Lead",
          name: "Microfirst",
          billing_street: "2335 N. Michigan Avenue",
          billing_city: "Anew York"
        },
        {
          required_time: "50",
          source: "Lead",
          name: "Dream Folks",
          billing_street: "2335 N. Michigan Avenue",
          billing_city: "New York"
        },
        {
          required_time: "60",
          source: "Lead",
          name: "Jhonson & Co",
          billing_street: "2335 Michigan Avenue",
          billing_city: "New York"
        },
        {
          required_time: "60",
          source: "Lead",
          name: "Microfirst",
          billing_street: "2335 N. Michigan Avenue",
          billing_city: "New Jersey"
        },
        {
          required_time: "120",
          source: "Lead",
          name: "First Alarm",
          billing_street: "2335 N. Michigan Avenue",
          billing_city: "Dallas"
        },
        {
          required_time: "120",
          source: "Lead",
          name: "Dream Folks",
          billing_street: "2335 Michigan Avenue",
          billing_city: "Austin"
        }
      ]
    };
  }
};
</script>