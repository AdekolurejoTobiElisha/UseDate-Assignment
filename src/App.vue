<template>
  <div>
    <p>Day: {{ getDay() }}</p>
    <p>Month: {{ getMonth() }}</p>
    <button @click="addDay">Add Day</button>
    <button @click="addMonth(1)">Add Month</button>
    <button @click="resetDate">Reset</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      initialDate: new Date(),
      date: new Date(),
    };
  },
  methods: {
    getDay() {
      return this.date.getDate();
    },
    getMonth() {
      return this.date.getMonth() + 1;
    },
    addDay() {
      const newDate = new Date(this.date);
      newDate.setDate(newDate.getDate() + 1);

      if (newDate.getMonth() !== this.date.getMonth()) {
        newDate.setDate(1);
      }
      this.date = newDate;
    },
    addMonth(numberOfMonths) {
      const newDate = new Date(this.date);
      newDate.setMonth(newDate.getMonth() + numberOfMonths);

      if (newDate.getMonth() !== (this.date.getMonth() + numberOfMonths) % 12) {
        newDate.setDate(0);
        newDate.setMonth(0);
      }
      this.date = newDate;
    },
    resetDate() {
      // Set both day and month to zero
      this.date.setDate(0);
      this.date.setMonth(0);
    },
  },
};
</script>
