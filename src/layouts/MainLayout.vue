<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          <q-icon name="lightbulb" class="q-mb-xs" /> Luz ERP
        </q-toolbar-title>

        <div>Administrador <q-icon name="account_circle" size="lg" /></div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :width="250"
      :breakpoint="500"
      class="bg-grey-4"
      bordered
    >
      <q-list>
        <q-item-label header>Menu</q-item-label>
        <q-item clickable @click="$router.push({ path: '/' })" v-ripple>
          <q-item-section avatar>
            <q-icon name="fa-solid fa-home" />
          </q-item-section>
          <q-item-section>Início</q-item-section>
        </q-item>

        <q-item
          clickable
          @click="$router.push({ path: '/notas_saida' })"
          v-ripple
        >
          <q-item-section avatar>
            <q-icon name="fa-solid fa-sack-dollar" />
          </q-item-section>
          <q-item-section>Notas de saída</q-item-section>
        </q-item>

        <q-item
          clickable
          @click="$router.push({ path: '/categorias' })"
          v-ripple
        >
          <q-item-section avatar>
            <q-icon name="fa-solid fa-list-ol" />
          </q-item-section>
          <q-item-section>Categorias</q-item-section>
        </q-item>

        <q-item
          clickable
          @click="$router.push({ path: '/fornecedores' })"
          v-ripple
        >
          <q-item-section avatar>
            <q-icon name="fa-solid fa-dolly" />
          </q-item-section>
          <q-item-section>Fornecedores</q-item-section>
        </q-item>

        <q-item clickable @click="$router.push({ path: '/produtos' })" v-ripple>
          <q-item-section avatar>
            <q-icon name="fa-solid fa-box-open" />
          </q-item-section>
          <q-item-section>Produtos</q-item-section>
        </q-item>

        <q-item clickable @click="$router.push({ path: '/clientes' })" v-ripple>
          <q-item-section avatar>
            <q-icon name="fa-solid fa-users" />
          </q-item-section>
          <q-item-section>Clientes</q-item-section>
        </q-item>

        <q-separator />
        <q-item clickable @click="logout" v-ripple position="bottom">
          <q-item-section avatar>
            <q-icon name="logout" />
          </q-item-section>
          <q-item-section> Sair </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { useQuasar } from "quasar";
import { defineComponent, onMounted, ref } from "vue";
import { useRouter } from "vue-router";
import { api } from "src/boot/axios";

defineComponent({ name: "MainLayout" });

const $q = useQuasar();
const router = useRouter();

const leftDrawerOpen = ref(false);

onMounted(() => {});

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}

function logout() {
  $q.loading.show();
  api
    .post("/lougout")
    .then(function () {
      document.cookie = "token_adm_luzerp=; expires=Thu, 01 Jan 1970;";
      router.push({ path: "/login" });
      $q.loading.hide();
    })
    .then(() => {
      $q.loading.hide();
    });
}
</script>
