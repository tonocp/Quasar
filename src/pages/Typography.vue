<template>
  <q-page class="flex column q-pa-md">
    <span class="text-h1">Headline 1</span>
    <span class="text-h2">Headline 2</span>
    <span class="text-h3">Headline 3</span>
    <span class="text-h4">Headline 4</span>
    <span class="text-h5">Headline 5</span>
    <span class="text-h6">Headline 6</span>

    <q-separator />

    <span class="text-subtitle1">Subtitle 1</span>
    <span class="text-subtitle2">Subtitle 2</span>

    <q-separator />

    <p class="text-body1">
      Officia ex laboris esse ut est officia deserunt nulla exercitation irure.
      Nisi duis nisi aliquip aliquip irure non officia non id. Labore dolore in
      duis laborum esse enim incididunt id est. Lorem tempor elit minim aute
      cupidatat enim enim ut culpa. Sint tempor elit nulla ea cupidatat sint ut
      nulla do fugiat consequat laboris.
    </p>

    <p class="text-body2">
      Velit magna proident esse cillum exercitation sint dolore do nisi officia
      anim anim. Dolor officia labore Lorem occaecat adipisicing duis labore in
      ea. Consectetur minim proident aute duis. Elit ad anim qui eu nostrud
      excepteur. Ex ut reprehenderit adipisicing ad fugiat aliquip et aliquip
      enim laboris.
    </p>

    <q-separator />

    <span class="text-weight-thin">Commodo culpa do excepteur esse.</span>
    <span class="text-weight-light"
      >Eu ipsum consectetur quis qui Lorem irure ipsum nulla velit est in.</span
    >
    <span class="text-weight-regular">Magna dolor ex velit sunt.</span>
    <span class="text-weight-medium"
      >Dolore enim do dolore adipisicing officia pariatur voluptate est
      consectetur magna nulla culpa.</span
    >
    <span class="text-weight-bold"
      >Nulla qui non pariatur aliquip ad labore.</span
    >
    <span class="text-weight-bolder"
      >Aute ipsum ut quis fugiat sit cupidatat voluptate magna et ex magna
      incididunt proident.</span
    >

    <q-btn
      class="q-mt-md"
      color="primary"
      :label="sideMenuOpen ? 'Cerrar menú lateral' : 'Abrir menú lateral'"
      @click="toggleSideMenu"
    />
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

import useUI from "../composables/useUI";

export default defineComponent({
  name: "Typography",

  setup() {
    const { sideMenuOpen, toggleSideMenu } = useUI();

    return {
      sideMenuOpen,

      toggleSideMenu,
    };
  },
});
</script>
