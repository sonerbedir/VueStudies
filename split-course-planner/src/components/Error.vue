<template>
  <div v-if="isError" class="alert" role="alert" >Kurs adı boş bırakılamaz</div>
</template>

<script>
export default {
  props: ['isError']
}
</script>