<template>
    <v-card class="mx-auto"  max-width="100%" :class="bgClass">
      <v-layout column>
        <v-app-bar
          color="teal-darken-1"
          
        >
          <!-- <template v-slot:image>
            <v-img
              gradient="to top right, rgba(19,84,122,.8), rgba(128,208,199,.8)"
            ></v-img>
          </template>
   -->
          <template v-slot:prepend>
            <v-app-bar-nav-icon></v-app-bar-nav-icon>
          </template>
  
          <v-app-bar-title><NuxtLink to="/">Rakaeiz</NuxtLink></v-app-bar-title>
  
          <v-spacer></v-spacer>
  
          <!-- زر تبديل الوضع مع الأيقونة المناسبة -->
          <v-btn icon @click="toggleColorMode" :class="locale == 'ar-AR'? 'md:ml-2' : 'md:mr-2'">
            <v-icon>{{ colorMode === 'dark' ? 'mdi-white-balance-sunny' : 'mdi-moon-waning-crescent' }}</v-icon>
          </v-btn>
          <div :class="locale == 'ar-AR'? 'ml-4' : 'mr-4'" class="flex items-center gap-1">
    <button @click="$i18n.setLocale('en-US')">English</button>
    <h1>-</h1>
    <button @click="$i18n.setLocale('ar-AR')">عربي</button>
  </div>
          <!-- <v-btn icon>
            <v-icon>mdi-magnify</v-icon>
          </v-btn> -->
  
          <!-- <v-btn icon>
            <v-icon>mdi-heart</v-icon>
          </v-btn>
  
          <v-btn icon>
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn> -->
        </v-app-bar>
  
        <v-main class="w-100 h-screen">
          <slot />
        </v-main>
      </v-layout>
    </v-card>
  </template>
  
  <script setup lang="ts">
  import { ref, watch, computed } from 'vue'
  const {locale} = useI18n()
  // تحديد وضع اللون الحالي
  const colorMode = ref<'light' | 'dark'>('light')
  
  // تحديث الوضع اللوني بناءً على الحالة
  watch(colorMode, (newValue) => {
    document.body.classList.toggle('dark', newValue === 'dark')
  })
  
  // لتغيير الوضع اللوني
  function toggleColorMode() {
    colorMode.value = colorMode.value === 'dark' ? 'light' : 'dark'
  }
  
  // تحديد فئة الخلفية بناءً على وضع اللون
  const bgClass = computed(() => {
    return colorMode.value === 'dark' ? 'bg-dark' : 'bg-light'
  })
  </script>
  
  <style scoped>
  /* تعريف أنماط الخلفية */
  .bg-dark {
    background-color: #1e1e1e;
    color: white;
  }
  
  .bg-light {
    background-color: #f5f5f5;
    color: black;
  }
  </style>
  