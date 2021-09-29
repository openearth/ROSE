<template>
  <div class="home">
    <v-navigation-drawer
      app
      clipped
      permanent
      width="350"
    >
      <v-container fluid>
        <v-row no-gutters>
          <v-col cols="5" align-self="center">
            <v-img
              width="110"
              height="50"
              contain
              src="/assets/images/deltares-logo.png"
            />
          </v-col>
        </v-row>
        <app-divider />
      </v-container>
    </v-navigation-drawer>
  </div>
</template>

<script>

  import AppDivider from '~/components/AppDivider/AppDivider'



  export default {
    name: 'Home',
    components: {
      AppDivider,

    },
  }
</script>
