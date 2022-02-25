<!-- ======= TEMPLATE ======= -->
<template>
  <custom-header title="Courses"></custom-header>
  <div class="parent">
    <div v-for="(course, index) in courses" v-bind:key="index">
      <card class="mt-4" :image="course.image">
        <template #title>
          {{ course.title }}
        </template>
        <template #body>
          {{ course.description }}
        </template>
        <template #end>
          <div class="d-grid gap-2 d-md-flex justify-content-md-right">
            <button class="btn btn-success"> View Course</button>
            <button class="btn btn-primary" @click="toQuiz(course.title,course.id)"> Quiz</button>
          </div>
        </template>
      </card>
    </div>
  </div>
</template>

<!-- ======= SCRIPT ======= -->
<script>
import CustomHeader from '../components/Header.vue'
import Card from '../components/Card.vue'

export default {
  components:
      {
        CustomHeader,
        Card
      },
  methods: {
    toQuiz(title,id) {
      this.$router.push({
        name: "Quiz",
        query: {title: title,id:id}
      })
    }
  },
  data() {
    return {
      courses:this.$store.state.courses
    }
  },
}
</script>

<!-- ======= STYLE ======= -->
<style scoped>
.card {
  width: 34rem;
}

.parent {
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-wrap: wrap;
  width: 100%;
  flex: 1;
}

</style>