<template>
  <div class="dashboard">
    <h1 class="subtitle-1 grey--text">
      This is <span class="red--text font-weight-bold">Dashboard</span>
    </h1>

    <v-container class="my-5">
      <v-row class="mb-4 ml-2">
        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              text
              small
              color="grey"
              v-bind="attrs"
              v-on="on"
              @click="bySort('title')"
            >
              <v-icon>mdi-folder</v-icon>
              <span class="caption text-lowercase grey--text pl-1">By project name</span>
            </v-btn>
          </template>
          <span>Sort projects by project name</span>
        </v-tooltip>

       <v-tooltip top>
         <template v-slot:activator="{on , attrs}">
           <v-btn text small color="grey" v-on="on" v-bind="attrs" @click="bySort('person')">
            <v-icon>mdi-account</v-icon>
            <span class="caption text-lowercase grey--text pl-1">By person</span>
          </v-btn>
         </template>
        <span>Sort projects by person name</span>
       </v-tooltip>

        
      </v-row>
      <v-card v-for="project in projects" :key="project.title">
        <v-row :class="`pa-3  ma-0  project ${project.status}`">
          <v-col cols="12" md="6">
            <h2 class="caption grey--text">Project Title</h2>
            <span class="font-weight-bold subtitle-2">{{ project.title }}</span>
          </v-col>

          <v-col cols="12" sm="4" md="2">
            <h2 class="caption grey--text">Person</h2>
            <span class="font-weight-bold subtitle-2">{{
              project.person
            }}</span>
          </v-col>

          <v-col cols="12" sm="4" md="2">
            <h2 class="caption grey--text">Due By</h2>
            <span class="font-weight-bold subtitle-2">{{ project.due }}</span>
          </v-col>

          <v-col cols="12" sm="4" md="2">
            <div align="right">
              <v-chip
                small
                :class="`${project.status} tes white--text my-2 caption`"
                >{{ project.status }}</v-chip
              >
            </div>
          </v-col>
        </v-row>
        <v-divider></v-divider>
      </v-card>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      projects: [
        {
          title: "Design a new project",
          person: "Mohammed Ali",
          due: "15-5-2021",
          status: "ongoing",
        },
        {
          title: "Backend & Frontend",
          person: "Talal Taha",
          due: "8-10-2021",
          status: "complete",
        },
        {
          title: "Full Stack",
          person: "Nadir Almahdy",
          due: "1-11-2021",
          status: "complete",
        },
        {
          title: "Web Devoloper",
          person: "X Man",
          due: "1-1-2021",
          status: "overdue",
        },
      ],
    };
  },
  methods: {
    bySort(prop) {
      // a > b => 1   a < b  => -1
      this.projects.sort((a, b) => (a[prop] < b[prop] ? -1 : 1));
    },
  },
};
</script>

<style>
/* .project{
  margin: 0;
} */
.project.ongoing {
  border-left: 4px solid darkorange;
}
.project.overdue {
  border-left: 4px solid rgb(50, 213, 224);
}
.project.complete {
  border-left: 4px solid seagreen;
}

.theme--light.v-chip:not(.v-chip--active).ongoing {
  background: darkorange;
}
.theme--light.v-chip:not(.v-chip--active).overdue {
  background: rgb(50, 213, 224);
}
.theme--light.v-chip:not(.v-chip--active).complete {
  background: seagreen;
}
</style>
