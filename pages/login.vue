<template>
    <div class="flex items-center justify-center my-auto h-full">
      <div class="shadow-lg px-20 py-10 card">
        <h2 class="mb-10 text-3xl  text-center">{{ $t('Login') }}</h2>
        <form @submit.prevent="login">
          <div class="flex flex-col gap-4">
            <div class="flex flex-col md:flex-row items-center gap-4">
              <label for="mobile" class="md:w-1/4 text-xl">{{ $t('Mobile Number') }}</label>
              <InputText id="mobile" v-model="mobile" type="text" class="flex-1 p-inputtext-lg"  />
            </div>
            <div class="flex flex-col md:flex-row items-center gap-4">
              <label for="password" class="md:w-1/4 text-xl">{{ $t('Password') }}</label>
              <InputText id="mobile" v-model="mobile" type="text" class="flex-1 p-inputtext-lg"  />
            </div>
          </div>
          <div class="flex justify-end mt-6">
            <Button :label="$t('Login')" icon="pi pi-sign-in" class="p-button-lg bg-teal-darken-1 text-center mx-auto" />
          </div>
        </form>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const mobile = ref('')
  const password = ref('')
  
  const login = () => {
    console.log('Attempting to login with:', { mobile: mobile.value, password: password.value })
    // هنا يمكنك إضافة الكود الخاص بمعالجة عملية تسجيل الدخول
  }
  </script>
  
  <style scoped>
  .card {
    padding: 4rem;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    max-width: 600px;
    width: 100%;
  }
  .mb-10 {
    margin-bottom: 2.5rem;
  }
  .text-3xl {
    font-size: 2rem;
  }
  .text-xl {
    font-size: 1.25rem;
  }
  .mt-6 {
    margin-top: 1.5rem;
  }
  </style>
  