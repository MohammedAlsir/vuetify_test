<template>
  <div class="team">
    <h1 class="subtitle-1 grey--text">
      This is <span class="red--text font-weight-bold">Team</span>
    </h1>

    <v-container class="my-5">
      <v-row>
        <v-col
          cols="12"
          sm="6"
          md="4"
          lg="3"
          v-for="person in team"
          :key="person.name"
        >
          <v-card>
             <v-responsive   class="text-center pt-4">
              <v-avatar class="grey lighten-3" size="100">
                <v-img :src="person.avatar"></v-img>
              </v-avatar>
            </v-responsive>
            <v-card-title class="justify-center">{{person.name}}</v-card-title>
            <v-card-subtitle class="text-center pt-2">{{person.role}}</v-card-subtitle>
            <v-card-actions>
              <v-row>

                <v-col class="text-left">
                  <v-btn plain class="ma-1" color="red lighten-2">
                    <v-icon small left>mdi-chat</v-icon>
                    <span class="text-capitalize">Message</span>
                  </v-btn>
                </v-col>
                
                <v-col class="text-right">
                  <v-btn plain class="ma-1 text-right" color="green lighten-2">
                    <v-icon small left>mdi-phone</v-icon>
                    <span class="text-capitalize">Call</span>
                  </v-btn>
                </v-col>

              </v-row>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      team: [
        { name: "Mohammed Alsir", role: "Web devoloper" , avatar:'/images/b.jpg'},
        { name: "Yaser Omar", role: "Frontend devoloper" , avatar:'/images/c.jpg'},
        { name: "Alhadi Tariq", role: "Backend devoloper" , avatar:'/images/d.jpg'},
        { name: "Ahemd Abdo", role: "Network" , avatar:'/images/l.jpg'},
        { name: "Talal Saad", role: "Sales guru" , avatar:'/images/n.jpg'},
      ],
    };
  },
};
</script>
