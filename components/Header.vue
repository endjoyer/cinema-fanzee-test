<template>
  <header class="header">
    <h1 @click="goToHome">Test Task</h1>
  </header>
</template>

<script setup>
import { useRouter } from 'vue-router';

const router = useRouter();

const goToHome = () => {
  router.push('/');
};
</script>

<style scoped>
.header {
  box-sizing: border-box;
  background: #292d32;
  padding: 16px 48px;
  position: fixed;
  width: 100%;
  min-height: 100px;
  top: 0;
  z-index: 1000;
  text-align: left;
  color: #fff;
  display: flex;
  align-items: center;
}
.header h1 {
  cursor: pointer;
  font-family: Roboto;
  font-size: 32px;
  font-weight: 700;
  line-height: 37.5px;
  margin: 0;
}
</style>
