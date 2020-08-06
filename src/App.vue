<template>
  <v-app>
    <v-navigation-drawer app>
      <!-- -->
      <p>navigation drawer</p>
    </v-navigation-drawer>

    <v-app-bar app>
      
      <p>app bar</p>
    </v-app-bar>
<!-- Sizes your content based upon application components -->
    <v-main>
      <!-- Provides the application the proper gutter -->
      <v-container fluid>
        <!-- If using vue-router -->
        <router-view></router-view>
      </v-container>
    </v-main>

    <v-footer app>
      <!-- -->
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      message: "RMUTL"
    };
  }
};
</script>

<style>
</style>