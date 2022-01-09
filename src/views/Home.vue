<template>
  <div class="home">
    <year-progress-bar
      :percent="percents.yearPercent"
    />
    <month-progress-bar
      :percent="percents.monthPercent"
    />
    <day-progress-bar
      :percent="percents.dayPercent"
    />
    <hour-progress-bar
      :percent="percents.hourPercent"
    />
    <minute-progress-bar
      :percent="percents.minutePercent"
    />
  </div>
</template>

<script lang="ts">
import { reactive } from 'vue';
import YearProgressBar from '@/components/ProgressBar/YearProgressBar.vue';
import MonthProgressBar from '@/components/ProgressBar/MonthProgressBar.vue';
import DayProgressBar from '@/components/ProgressBar/DayProgressBar.vue';
import HourProgressBar from '@/components/ProgressBar/HourProgressBar.vue';
import MinuteProgressBar from '@/components/ProgressBar/MinuteProgressBar.vue';

export default {
  name: 'Home',
  components: {
    YearProgressBar,
    MonthProgressBar,
    DayProgressBar,
    HourProgressBar,
    MinuteProgressBar
  },
  setup(){
    const percents = reactive({
      minutePercent: '',
      hourPercent: '',
      dayPercent: '',
      monthPercent: '',
      yearPercent: ''
    });
    let currentDate = 0;

    const setMinutePercent = (timeNow:Date) => {
      const currentMinuteStartPoint = 
        new Date(
          timeNow.getFullYear(), 
          timeNow.getMonth(), 
          timeNow.getDate(), 
          timeNow.getHours(),
          timeNow.getMinutes()
        ).getTime();
      const minuteGage = (timeNow.getTime() - currentMinuteStartPoint)/(1000*60);
      percents.minutePercent = `${(minuteGage*100).toFixed(1)}%`;
    }
    const setHourPercent = (timeNow:Date) => {
      const currentTimeStartPoint = 
        new Date(
          timeNow.getFullYear(), 
          timeNow.getMonth(), 
          timeNow.getDate(), 
          timeNow.getHours()
        ).getTime();
      const hourGage = (timeNow.getTime() - currentTimeStartPoint)/(1000*60*60);
      percents.hourPercent = `${(hourGage*100).toFixed(1)}%`;
    }
    const setDayPercent = (timeNow:Date) => {
      const currentDayStartPoint = 
        new Date(
          timeNow.getFullYear(), 
          timeNow.getMonth(), 
          timeNow.getDate()
        ).getTime();
      const dayGage = (timeNow.getTime() - currentDayStartPoint)/(1000*60*60*24);
      percents.dayPercent = `${(dayGage*100).toFixed(1)}%`;
    }
    const setMonthPercent = (timeNow:Date) => {
      const currentMonthStartPoint = new Date(timeNow.getFullYear(), timeNow.getMonth(), 1).getTime();
      const nextMonth = new Date(timeNow.getFullYear(), timeNow.getMonth() + 1, 1).getTime();
      const lengthOfOneMonth = nextMonth - currentMonthStartPoint;
      const monthGage = (timeNow.getTime() - currentMonthStartPoint)/lengthOfOneMonth;
      percents.monthPercent = `${(monthGage*100).toFixed(2)}%`;
    }
    const setYearPercent = (timeNow:Date) => {
      const currentYearStartPoint = new Date(timeNow.getFullYear(), 0, 1).getTime();
      const nextYear = new Date(timeNow.getFullYear() + 1, 0, 1).getTime();
      const lengthOfOneYear = nextYear - currentYearStartPoint;
      const yearGage = (timeNow.getTime() - currentYearStartPoint)/lengthOfOneYear;
      percents.yearPercent = `${(yearGage*100).toFixed(2)}%`;
    }



    setInterval(() => {
      const timeNow = new Date();
      setMinutePercent(timeNow);
      setHourPercent(timeNow);
      setDayPercent(timeNow);

      if (timeNow.getDate() != currentDate) {
        currentDate = timeNow.getDate();
        setMonthPercent(timeNow);
        setYearPercent(timeNow);
      }
    }, 200);

    return {
      percents
    }
  }
};
</script>
