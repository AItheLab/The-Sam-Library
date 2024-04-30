<template>
  <div class="calendar">
    <!-- Calendar Header -->
    <div class="calendar-header">
      <button @click="prevMonth" class="nav-button">❮</button>
      <h2 class="month-year">{{ formattedDate }}</h2>
      <button @click="nextMonth" class="nav-button">❯</button>
    </div>

    <!-- Day Names -->
    <div class="day-names">
      <span>S</span><span>M</span><span>T</span><span>W</span><span>T</span><span>F</span><span>S</span>
    </div>

    <!-- Days Grid -->
    <div class="days-grid">
      <button 
        v-for="day in daysOfMonth" 
        :key="day.date" 
        :class="{'today': day.isToday, 'selected': day.isSelected}"
        @click="selectDate(day)">
        {{ day.date ? day.date.getDate() : ''}}
      </button>
    </div>

    <!-- Calendar Footer -->
    <div class="calendar-footer">
      <button @click="cancel">Cancel</button>
      <button @click="confirm">OK</button>
    </div>
  </div>
</template>

  
<script setup>
import { ref, computed } from 'vue';

const selectedDate = ref(new Date());
const today = new Date();

const formattedDate = computed(() => {
  return selectedDate.value.toLocaleDateString('en-US', {
    month: 'long',
    year: 'numeric'
  });
});

const daysOfMonth = computed(() => {
  const days = [];
  const year = selectedDate.value.getFullYear();
  const month = selectedDate.value.getMonth();
  const firstDay = new Date(year, month, 1);
  const startDayOfWeek = firstDay.getDay();
  const totalDays = new Date(year, month + 1, 0).getDate();

  for (let i = 0; i < startDayOfWeek; i++) {
    days.push({ date: null });
  }

  for (let day = 1; day <= totalDays; day++) {
    const date = new Date(year, month, day);
    days.push({
      date,
      isToday: date.toDateString() === today.toDateString(),
      isSelected: date.toDateString() === selectedDate.value.toDateString()
    });
  }

  return days;
});

function selectDate(day) {
  selectedDate.value = new Date(day.date);
}

function prevMonth() {
  selectedDate.value.setMonth(selectedDate.value.getMonth() - 1);
}

function nextMonth() {
  selectedDate.value.setMonth(selectedDate.value.getMonth() + 1);
}
</script>


  
<style scoped>
.calendar {
  width: 300px;
  background: #fff;
  border-radius: 4px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
  font-family: 'Roboto', sans-serif;
}

.calendar-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 16px;
  background: #6200ee; /* Material Design Primary Color */
  color: white;
}

.nav-button {
  background: none;
  border: none;
  color: white;
  cursor: pointer;
  font-size: 24px;
}

.month-year {
  font-size: 16px;
  font-weight: 500;
}

.day-names {
  display: flex;
  background-color: #f0f0f0;
  padding: 10px 0;
}

.day-names span {
  flex: 1;
  text-align: center;
  font-size: 12px;
  color: #616161;
}

.days-grid {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  padding: 8px;
}

.days-grid button {
  height: 32px;
  background: none;
  border: none;
  color: #616161;
  cursor: pointer;
}

.days-grid button.today {
  border: 1px solid #6200ee;
}

.days-grid button.selected {
  background-color: #6200ee;
  color: white;
}

.calendar-footer {
  display: flex;
  justify-content: flex-end;
  padding: 8px 16px;
  border-top: 1px solid #e0e0e0;
}

.calendar-footer button {
  background: #6200ee;
  color: white;
  border: none;
  padding: 8px 16px;
  margin-left: 8px;
  cursor: pointer;
  border-radius: 4px;
}
</style>

  