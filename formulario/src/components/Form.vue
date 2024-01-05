<script setup lang="ts">
import { reactive, ref } from "vue";
import Label from "./Label.vue";
import Input from "./Input.vue";
import Button from "./Button.vue";

// const nombre = ref("");
// const apellido = ref("");

const data = reactive({
  name: "",
  lastname: "",
  email: "",
  password: "",
});

const showResult = ref(false);

const handleSubmit = () => {
  showResult.value = true;
};
</script>

<template>
  <form @submit.prevent="handleSubmit" class="mt-10">
    <div class="w-full flex flex-col items-center justify-center px-8 gap-y-8">
      <div class="flex flex-col md:w-2/5 lg:w-1/4 w-full">
        <Label title="Name" dynamicFor="name" />
        <div>
          <Input
            v-model="data.name"
            inputId="name"
            placeholder="Joe"
            :type="'text'"
          />
        </div>
      </div>
      <div class="flex flex-col md:w-2/5 lg:w-1/4 w-full">
        <Label title="Last Name" dynamicFor="lastname" />
        <div>
          <Input
            v-model="data.lastname"
            inputId="lastname"
            placeholder="Doe"
            :type="'text'"
          />
        </div>
      </div>
      <div class="flex flex-col md:w-2/5 lg:w-1/4 w-full">
        <Label title="Email" dynamicFor="email" />
        <div>
          <Input
            v-model="data.email"
            inputId="email"
            placeholder="Doe@gmail.com"
            :type="'email'"
          />
        </div>
      </div>
      <div class="flex flex-col md:w-2/5 lg:w-1/4 w-full">
        <Label title="Password" dynamicFor="password" />
        <div>
          <Input
            v-model="data.password"
            inputId="password"
            placeholder="********"
            :type="'password'"
          />
        </div>
      </div>
      <div class="flex md:w-2/5 lg:w-1/4 w-full mt-8">
        <Button title="Enviar" type="submit" />
      </div>
    </div>
  </form>
  <div v-if="showResult" class="flex flex-col items-center justify-center my-8">
    <span class="text-slate-100 font-bold uppercase">
      {{ data.name }} {{ data.lastname }}
    </span>
    <span class="text-slate-100 font-bold uppercase">
      {{ data.email }} {{ data.password }}
    </span>
  </div>
</template>
