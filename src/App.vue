<template>
  <div>
    <notifications group="g-login" />
    <template v-if="!$route.meta.allowAnonymous">
      <v-app id="inspire">
        <div class="app-container">
          <toolbar @toggle2NavigationBar="drawer = !drawer" />
          <navigation :toggle="drawer" />
          <v-content>
            <breadcrumbs />
            <router-view />
            <page-footer />
          </v-content>
        </div>
      </v-app>
    </template>
    <template v-else>
      <transition>
        <keep-alive>
          <router-view></router-view>
        </keep-alive>
      </transition>
    </template>
  </div>
</template>

<script>
// import Navigation from './components/core/NavigationDrawer.vue';
// import Toolbar from './components/core/Toolbar.vue';

export default {
  name: "App",
  data() {
    return {
      drawer: true
    };
  }
};
</script>

<style>
</style>
