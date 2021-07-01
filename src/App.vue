<template>
  <v-app>
    <Mynav />
    <v-main class="grey lighten-3">
      <div class="mx-4 my-5">
        <router-view/>
      </div>
    </v-main>
  </v-app>
</template>

<script>
import Mynav from '@/components/Mynav'
export default {
  name: 'App',

  data: () => ({
    //
  }),
  components:{Mynav}
};
</script>



