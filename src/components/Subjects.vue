<template>
    <div class="card">
    <div class="item">
        <i>
            <h1>POPIS PREDMETA</h1>
        </i>
        <div class="details">
            <table>
                <thead>
                    <tr>
                        <th>Ime predmeta</th>
                        <th>Predavač</th>
                        <th>Broj bodova</th>
                        <th> Detalji </th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="course in allCourses" :key="course.id">
                        <td>{{ course.name }}</td>
                        <td>{{ course.professor }}</td>
                        <td>{{ course.credits }}</td>
                        <td> <button id="show-modal" @click="onDetails(course.id)">Detalji</button></td>
                    </tr>
                </tbody>
                <tfoot>
                    <th>
                    </th>
                    <th></th>
                    <th></th>
                    <th>
                        Suma bodova : {{ sumOfCredits }}
                    </th>
                </tfoot>
            </table>
        </div>
        <transition name="modal">
    <details-modal v-if="showModal" @close="showModal = false" v-bind="allCourses[selectedCourse]" />
  </transition>
    </div>
</div>
</template>


<script>
import { computed } from '@vue/runtime-core';
import DetailsModal from './DetailsModal.vue';
import { useCourseStore } from '../stores/courses'
import { mapState } from 'pinia';
export default {
  components: { DetailsModal },
  data() {
    return {
      selectedCourse: null,
      showModal: false
    }
  },
  async created() {
    const { allCourses, fetchCourses } = useCourseStore();
    fetchCourses();
    return { allCourses }
  },

  computed: {
    sumOfCredits() {
        return this.allCourses.reduce((total, obj) => total + obj.credits, 0);
    },
    ...mapState(useCourseStore, ["allCourses"])
  },

  methods: {
    deleteCourse(id) {
        this.$emit('deleteCourse', {id: id})
    },
    onDetails(id) {
        this.selectedCourse = this.allCourses.findIndex((value) => value.id == id);
        this.showModal = true;
    }
  }
}
</script>

<style scoped>
.item {
    margin-top: 2rem;
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
}

table {
    border-collapse: collapse;
    width: 100%;
    font-family: Arial, sans-serif;
}

/* Styles for the table header */
th {
    background-color: #f2f2f2;
    color: #333333;
    text-align: left;
    padding: 8px;
    border-bottom: 1px solid #dddddd;
}

/* Styles for the table cells */
td {
    border-bottom: 1px solid #dddddd;
    padding: 8px;
    text-align: left;
}

/* Styles for the even rows */
tr:nth-child(even) {
    background-color: #f9f9f9;
}
</style>
