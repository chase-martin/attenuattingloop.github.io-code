<template>
  <div class="text-md-center">
    <v-avatar
      color="grey lighten-4"
      size="120"
    >
      <img
        :src="publicPath('/img/avatar.jpg')"
        alt="James Chase Martin"
      >
    </v-avatar>
  </div>
</template>

<script>
export default { name: 'Avatar' }
</script>

<style scoped>
  img{object-fit: cover;}
</style>
