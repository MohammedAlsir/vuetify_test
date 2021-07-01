<template>
  <div class="projec">
    <h1 class="subtitle-1 grey--text">
      This is <span class="red--text font-weight-bold">project</span>
    </h1>

    <v-container class="my-5">
      <v-expansion-panels >
        <v-expansion-panel v-for="project in myprojects" :key="project.person">
          <!-- Header -->
          <v-expansion-panel-header>
            {{ project.title }}
          </v-expansion-panel-header>
          <!-- Header -->
          <!-- content -->
          <v-expansion-panel-content class="grey--text">
            <div class="font-weight-bold">due by : {{project.person}}</div>
            <div>{{project.content}}</div>
          </v-expansion-panel-content>
          <!-- content -->
        </v-expansion-panel>
      </v-expansion-panels>
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
          content:
            "ipectetur adipisicing elit.  unde nisi illo assumenda voluptate? Aliquid sequi, sint et veniam dolorem cum nemo delectus esse reiciendis eos illo.",
        },
        {
          title: "Backend & Frontend",
          person: "Talal Taha",
          due: "8-10-2021",
          status: "complete",
          content:
            "This is ipectetur adipisicing elit.  unde nisi illo assumenda voluptate? Aliquid sequi, sint et tus esse reiciendis eos illo.",
        },
        {
          title: "Full Stack",
          person: "Nadir Almahdy",
          due: "1-11-2021",
          status: "complete",
          content:
            "Hello From ipectetur adipisicing elit.  unde nisi illo assumenda voluptate? Aliquid sequi, sint et veniam dolorem cum nemo delectus esse reiciendis eos illo.",
        },
        {
          title: "Web Devoloper",
          person: "X Man",
          due: "1-1-2021",
          status: "overdue",
          content:
            "Hi X-man ipectetur adipisicing elit.  unde nisi illo assumenda voluptate? Aliquid sequi, sint et veniam dolorem cum nemo delectus esse reiciendis eos illo.",
        },
      ],
    };
  },
  computed: {
    myprojects(){
      return this.projects.filter(project=>{
        return project.person ==='X Man'
      })
    }

  },

  // filters: {
  //     myfill(value) {
  //       return value.person ==='X Man'
  //     }
  // }
  

};
</script>
