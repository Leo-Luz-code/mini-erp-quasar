<template>
  <q-page
    class="window-height window-width row justify-center items-center custom-background"
  >
    <div class="column q-pa-lg">
      <div class="row">
        <q-card square class="shadow-24 glass-card" style="width: 400px">
          <q-card-section class="bg-primary">
            <h4 class="text-h5 text-white q-my-md text-center">
              Mini ERP - Login
            </h4>
          </q-card-section>
          <q-card-section>
            <q-form class="q-px-sm" @submit="entrar">
              <q-input
                ref="login"
                square
                clearable
                v-model="state.login"
                type="text"
                lazy-rules
                :rules="[
                  (val) => (val && val.length > 3) || 'Campo obrigatório',
                ]"
                label="E-mail"
              >
                <template v-slot:prepend>
                  <q-icon name="verified_user" />
                </template>
              </q-input>

              <q-input
                ref="password"
                square
                clearable
                v-model="state.senha"
                :type="state.passwordFieldType"
                lazy-rules
                :rules="[
                  (val) => (val && val.length > 5) || 'Campo obrigatório',
                ]"
                label="Senha"
              >
                <template v-slot:prepend>
                  <q-icon name="lock" />
                </template>
                <template v-slot:append>
                  <q-icon
                    :name="state.visibilityIcon"
                    @click="switchVisibility"
                    class="cursor-pointer"
                  />
                </template>
              </q-input>
              <q-card-actions>
                <q-btn
                  unelevated
                  size="lg"
                  color="primary"
                  type="submit"
                  class="full-width text-white"
                  label="Entrar"
                />
              </q-card-actions>
            </q-form>
          </q-card-section>
        </q-card>
      </div></div
  ></q-page>
</template>
