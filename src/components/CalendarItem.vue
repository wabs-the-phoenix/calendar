<template>
  <div class="mt-2">
    <div class="d-flex justify-content-between bg-secondary p-2 text-white fw-bold mt-5">
      <h3>{{ monthName }}</h3>
      <h3>{{ currentYear }}</h3>
    </div>
    <h4 class="row mb-3">
      <div v-for="day in weekDays" :key="day" class="col fw-bold text-center">
      {{ day }}</div>
      </h4>
    <div class="d-flex flex-wrap">
      <div v-for="num in startDays" :key="num" style="width: 14.28%" class="text-center mb-2"></div>
      <div v-for="num in monthDays" :key="num" style="width: 14.28%" class="text-center mb-2" :class="highlightPresentDate(num)">{{ num }}</div>
    </div>
    <div class="d-flex justify-content-between p-2 mt-2">
      <button class="btn btn-primary" @click="prev">Prev</button>
      <button class="btn btn-primary" @click="next">Next</button>
    </div>
  </div>
</template>

<script>
export default {
    data() {
      return {
        weekDays: ['Dim', 'Lun', 'Mar', 'Mer', 'Jeu', 'Ven', 'Sam'],
        currentMonth: new Date().getMonth(),
        currentDate: new Date().getDate(),
        currentYear: new Date().getFullYear(),
        presentDate: new Date(),
      }
    },
    computed: {
        monthDays() {
          return new Date(this.currentYear, this.currentMonth + 1, 0).getDate();
        },
        startDays() {
          let dayOfWeek = new Date(this.currentYear, this.currentMonth, 1).getDay();
          return dayOfWeek;
        },
        monthName() {
          return new Date(this.currentYear, this.currentMonth).toLocaleDateString('fr-FR', {month: 'long'})
        }
    },
    methods: {
      next() {
        if(this.currentMonth === 11) {
          this.currentMonth = 0;
          this.currentYear ++;
          return;
        }
        this.currentMonth++;
      },
      prev() {
        if(this.currentMonth === 0) {
          this.currentMonth = 11;
          this.currentYear --;
          return;
        }
        this.currentMonth--;
      },
      highlightPresentDate(num) {
        return this.presentDate.getDate() === num &&
         this.presentDate.getMonth() === this.currentMonth &&
         this.presentDate.getFullYear() === this.currentYear ?  'bg-primary text-white': '';
       
      }
    }
}
</script>

<style>

</style>