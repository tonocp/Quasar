<template>
  <q-page class="q-ma-md">
    <span class="text-h3">Forms</span>

    <q-separator spaced />

    <div class="row justify-center">
      <q-form
        @submit="onSubmit"
        @reset="onReset"
        class="q-gutter-xs col-xs-12 col-sm-12 col-md-6 q-pt-xl"
      >
        <q-input
          filled
          v-model="userForm.email"
          label="Correo electrónico"
          hint="Inserte un email válido"
          type="email"
          lazy-rules
          :rules="[
            (val) => (val && val.length > 0) || 'Este campo es requerido',
            isValidEmail,
          ]"
        />

        <q-input
          filled
          type="password"
          v-model="userForm.password1"
          label="Contraseña"
          lazy-rules
          :rules="[
            (val) => (val && val.length > 0) || 'Este campo es requerido',
          ]"
        />

        <q-input
          filled
          type="password"
          v-model="userForm.password2"
          label="Repetir Contraseña"
          lazy-rules
          :rules="[
            (val) => (val && val.length > 0) || 'Este campo es requerido',
            isSamePassword,
          ]"
        />

        <q-checkbox
          v-model="userForm.conditions"
          label="Acepto los términos y condiciones de uso"
          :style="
            userForm.errorInConditions && !userForm.conditions && 'color:red'
          "
        />

        <div class="row justify-end">
          <q-btn
            label="Reset"
            type="reset"
            color="primary"
            flat
            class="q-ml-sm"
          />
          <q-btn label="Submit" type="submit" color="primary" />
        </div>
      </q-form>
    </div>
  </q-page>
</template>

<script>
import { defineComponent, ref } from "vue";

import { useQuasar } from "quasar";

export default defineComponent({
  name: "Forms",
  setup() {
    const $q = useQuasar();
    $q.iconSet.field.error = "las la-exclamation-circle";

    const userForm = ref({
      email: "",
      password1: "",
      password2: "",
      conditions: false,
      errorInConditions: false,
    });

    return {
      userForm,

      onSubmit() {
        userForm.value.errorInConditions = false;

        if (!userForm.value.conditions) {
          $q.notify({
            message: "Debe de aceptar los términos y condiciones",
            icon: "las la-exclamation-circle",
          });
          userForm.value.errorInConditions = true;
          return;
        }
        console.log(userForm.value);
      },
      onReset() {
        userForm.value = {
          email: "",
          password1: "",
          password2: "",
          conditions: false,
          errorInConditions: false,
        };
      },

      isValidEmail(val) {
        const emailPattern =
          /^(?=[a-zA-Z0-9@._%+-]{6,254}$)[a-zA-Z0-9._%+-]{1,64}@(?:[a-zA-Z0-9-]{1,63}\.){1,8}[a-zA-Z]{2,63}$/;
        return emailPattern.test(val) || "El correo no parece ser válido";
      },

      isSamePassword(val) {
        return (
          val === userForm.value.password1 || "Las contraseñas no son iguales"
        );
      },
    };
  },
});
</script>
