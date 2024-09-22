<template>
<div>
  <h2 v-if="role === 'admin'">Quyền hạn của bạn là: Admin</h2>
  <h2 v-else-if="role === 'user'">Quyền hạn của bạn là: User</h2>
  <h2 v-else-if="role === 'guest'">Quyền hạn của bạn là: Guest</h2>
  </div>
</template>

<script setup>
    const role = 'user'
</script>

<style>

</style>