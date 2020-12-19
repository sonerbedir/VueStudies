<template>
  <header>Kurs Planlaması</header>
  <div class="container">
    <div class="course--planner-app--container">
      <div class="card">
        <div class="user--action--container">
          <search-bar @course-item-added="addCourse" />
        </div>
        <error :isError="error" />
      </div>
      <div class="card card-light mt-20">
        <h3>Aktif Kurslarım</h3>
        <ul class="list mt-20" id="courseList">
          <course-list-item :items="courseList" @is-completed="updateCourse" />
        </ul>
      </div>
      <div class="mt-10">
        <completed-course-info :completedCourses="courseInfo" />
      </div>
    </div>
  </div>
</template>

<script>
import SearchBar from "@/components/SearchBar";
import CourseListItem from "@/components/CourseListItem";
import Error from "@/components/Error";
import CompletedCourseInfo from "@/components/CompletedCourseInfo";
export default {
  name: "App",
  components: {
    SearchBar,
    CourseListItem,
    Error,
    CompletedCourseInfo,
  },
  data() {
    return {
      courseList: [],
      error: false,
      courseInfo: null,
    };
  },
  methods: {
    addCourse(item) {
      if (item.name === '') {
        this.error = true;
        setTimeout(() => {
          this.error = false;
        }, 2000);
      } else {
        this.courseList.push(item);
        this.updateCourseInfo();
      }
    },
    updateCourse() {
      this.updateCourseInfo();
    },
    updateCourseInfo() {
      const completedCoursesCount = this.courseList.filter((x) => {
        return x.isCompleted;
      }).length;
      const uncompletedCoursesCount = this.courseList.filter((x) => {
        return !x.isCompleted;
      }).length;
      this.courseInfo = `Tamamlanan kursların sayısı: ${completedCoursesCount} | Tamamlanmayan kursların sayısı: ${uncompletedCoursesCount}`;
    },
  },
};
</script>

<style>
.bgrdanger {
  background-color: red !important;
  color: white;
}

.bgrsuccess {
  background-color: green !important;
  color: white;
}
.alert {
  background-color: #f8d7da;
  color: #8a3d44;
  border: 1px solid lightgrey;
  border-radius: 5px;
  margin: 10px 0;
  padding: 10px;
}
</style>
