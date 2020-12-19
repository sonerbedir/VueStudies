<template>
  <div class="form-group">
    <label>Kursun Adı</label>
    <input v-model="newCourse" type="text" @keypress.enter="addCourse" />
  </div>
  <button class="btn-primary" @click="addCourse">Kurs Ekle</button>
</template>

<script>
export default {
    data() {
        return {
            newCourse: ''
        }
    },
    methods: {
        addCourse() {
            this.$emit('course-item-added', {'name': this.newCourse, 'isCompleted': false});
            this.newCourse=""
        }
    }
}
</script>