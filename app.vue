
<template>
<NuxtLayout >
<NuxtPage :style="locale == 'ar-AR'? 'direction: rtl' : ''"/>
</NuxtLayout>
</template>

<script setup>
const { locale } = useI18n()
</script>