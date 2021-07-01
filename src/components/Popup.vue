<template>
  <v-dialog v-model="dialog" width="500">
    <template v-slot:activator="{ on, attrs }">
      <v-btn color="red lighten-2" dark v-bind="attrs" v-on="on">
        Add new project
      </v-btn>
    </template>
    <!--  -->
    <v-card>
      <v-card-title class="text-h5 grey lighten-2">
        Add new project
      </v-card-title>

      <v-card-text>
        <v-form class="mt-2">
          <v-text-field
            prepend-inner-icon="mdi-pen"
            dense
            outlined
            class="mb-1 mt-5"
            label="Title"
            hint="Enter Your Title"
            v-model="title"
          ></v-text-field>
          <v-textarea
            prepend-inner-icon="mdi-book"
            dense
            outlined
            class="mb-1"
            hint="Enter Your Content"
            v-model="content"
            label="Content"
          ></v-textarea>
          
          <v-menu
            ref="menu"
            v-model="menu"
            :close-on-content-click="false"
            :return-value.sync="date"
            transition="scale-transition"
            offset-y
            min-width="auto">
            <template v-slot:activator="{ on, attrs }">
              <v-text-field
                v-model="date"
                label="Picker in menu"
                prepend-icon="mdi-calendar"
                readonly
                v-bind="attrs"
                v-on="on"
              ></v-text-field>
            </template>
            <v-date-picker v-model="date"  >
              <v-spacer></v-spacer>
              <v-btn text color="primary" @click="menu = false"> Cancel </v-btn>
              <v-btn text color="primary" @click="$refs.menu.save(date)">
                OK
              </v-btn>
            </v-date-picker>
          </v-menu>
          <v-divider></v-divider>

          <v-card-actions class="mb-0 pb-0">
            <v-spacer></v-spacer>
            <v-btn color="primary" text @click="submit"> I accept </v-btn>
          </v-card-actions>
        </v-form>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      content: "",
      date: new Date(Date.now() - new Date().getTimezoneOffset() * 60000)
        .toISOString()
        .substr(0, 10),
      menu: false,
    };
  },
  methods: {
    submit() {
      console.log(this.title + " " + this.content);
    },
  },
};
</script>
