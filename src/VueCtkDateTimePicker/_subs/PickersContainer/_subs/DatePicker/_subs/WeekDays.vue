<template>
  <div
    :class="{'is-dark': dark}"
    class="week-days flex"
  >
    <div
      v-for="(weekDay, index) in weekDays"
      :key="index"
      class="flex-1 text-muted lm-fs-12 flex justify-content-center align-center week-days-container"
    >
      {{ weekDay | formatWeekDay }}
    </div>
  </div>
</template>

<script>
  export default {
    name: 'WeekDays',
    props: {
      weekDays: { type: Array, default: () => ([]), required: true },
      dark: { type: Boolean, default: null }
    },
    filters: {
      formatWeekDay(value){
        if(value){
          switch(value){
            case 'Sun':
              return '日';
            break;
            case 'Mon':
              return '一';
            break;
            case 'Tue':
              return '二';
            break;
            case 'Wed':
              return '三';
            break;
            case 'Thu':
              return '四';
            break;
            case 'Fri':
              return '五';
            break;
            case 'Sat':
              return '六';
            break;
          }
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
  .week-days {
    height: 41px;
    text-transform: capitalize;
    &.is-dark .week-days-container {
      color: #a8a8a8 !important;
    }
  }
  @media screen and (max-width: 415px) {
    &:not(.inline) {
      .datepicker-week {
        height: 21px !important;
      }
    }
  }
</style>
