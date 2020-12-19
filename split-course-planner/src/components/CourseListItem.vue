<template>
  <li
    v-for="course in items"
    :key="course.name"
    class="course-item list-item"
    :class="{ bgrsuccess: course.isCompleted, bgrdanger: !course.isCompleted }"
  >
    <span>{{ course.name }}</span>
    <input type="checkbox" v-model="course.isCompleted" @change="courseCompleted" />
  </li>
</template>

<script>
export default {
    props: ['items'],
    methods: {
        courseCompleted() {
            this.$emit('is-completed');
        }
    }
}
</script>