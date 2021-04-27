<script>
import { Radar } from 'vue-chartjs'

export default {
  extends: Radar,
  name: 'SkillChart',
  data () {
    return {
      data: {
        labels: [
          'Objectice-C',
          'Swift',
          'Java',
          'Kotlin',
          'PHP',
          'C/C++'
        ],
        datasets: [
          {
            // type: 'radar',
            backgroundColor: 'rgba(60,141,188,0.2)',
            borderColor: 'rgba(60,141,188,0.8)',
            // pointRadius: false,
            // pointColor: '#3b8bba',
            // pointStrokeColor: 'rgba(60,141,188,1)',
            // pointHighlightFill: '#fff',
            // pointHighlightStroke: 'rgba(60,141,188,1)',
            data: [3, 3, 3, 3, 3, 3],
            label: 'Programming SKill'
          }
        ]
      },
      options: {
        maintainAspectRatio: true,
        spanGaps: false,
        elements: {
          line: {
            tension: 0.000001
          }
        },
        plugins: {
          filler: {
            propagate: false
          }
        }
      }
    }
  },
  mounted () {
    this.renderChart(this.data, this.options)
  }
}
</script>
