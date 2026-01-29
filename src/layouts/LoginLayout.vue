<template>
  <q-layout view="lHh LpR lFf" container>
    <q-page-container class="container-fluid">
      <router-view> </router-view>
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { defineComponent } from "vue";

defineComponent({
  name: "LoginLayout",
});
</script>
