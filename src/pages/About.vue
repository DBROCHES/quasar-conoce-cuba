<!-- eslint-disable vue/multi-word-component-names -->

<template>
  <q-page padding>
    <h1>Hola About</h1>
    <q-list padding>
      <q-item clickable v-ripple to="/" active-class="my-menu-link" exact>
        <q-item-section avatar>
          <q-icon name="inbox" />
        </q-item-section>
        <q-item-section> Inicio</q-item-section>
      </q-item>

      <q-item clickable v-ripple to="/about" active-class="my-menu-link">
        <q-item-section avatar>
          <q-icon name="star" />
        </q-item-section>
        <q-item-section> About </q-item-section>
      </q-item>

      <q-item clickable v-ripple to="/vehicle" active-class="my-menu-link">
        <q-item-section avatar>
          <q-icon name="send" />
        </q-item-section>
        <q-item-section> Vehicle </q-item-section>
      </q-item>

      <q-expansion-item icon="drafts" label="Drafts" caption="">
        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="drafts" />
          </q-item-section>
          <q-item-section> Submenu Item 1 </q-item-section>
        </q-item>
        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="drafts" />
          </q-item-section>
          <q-item-section> Submenu Item 2 </q-item-section>
        </q-item>
      </q-expansion-item>
    </q-list>
  </q-page>
</template>
