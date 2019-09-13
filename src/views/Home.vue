<template lang="pug">
  div
    div(style="margin: 20px 0;")
      date-range-picker(:to="'2019-06-26T00:00:00.000+02:00'" :amountCalendars="2" :future="true" :past="false" :presets="['today','yesterday','last7days','last30days','pastWeek','pastMonth','custom']" :from="'2019-05-26T00:00:00.000+02:00'"  @update="checkUpdate" locale="es" submit-title="Actualiser" :panel="$route.query.panel" begin="2017-02-19T00:00:00.000+01:00")
      //- pre Date Picker 1
      //- date-range-picker(:to="$route.query.to" :from="$route.query.from" @update="checkUpdate" :past="false" :dark="false")
</template>

<script lang="ts">
  import { Component, Vue } from 'vue-property-decorator'
  import DateRangePicker from '@/components/DateRangePicker.vue'

  @Component({
    components: {
      DateRangePicker
    },
  })
  export default class Home extends Vue {
    theme = {
      primary: '#46C3A3',
      secondary: '#2D3E50',
      ternary: '#93A0BD',
      light: '#ffffff',
      border: '#e6e6e6',
      dark: '#000000',
      hovers: {
        day: '#CCC',
        range: '#e6e6e6'
      }
    }
    checkUpdate(values) {
      this.$router.push({ query: Object.assign({}, this.$route.query, {
        to: values.to,
        from: values.from,
        panel: values.panel
      }) })
    }
  }
</script>
