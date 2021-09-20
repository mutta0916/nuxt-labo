<script>
import { Line } from 'vue-chartjs'
export default {
  extends: Line,
  data(){
    return {
        chartdata: {
            labels: ['１月', '２月', '３月', '４月', '５月', '６月', '７月', '８月', '９月', '１０月', '１１月', '１２月'],
            datasets: [
                {
                label: ['人口'],
                backgroundColor: 'rgba(0,0,255,0)',
                data: [10, 40, 20, 100, 30, 50, 70, 40, 50, 90, 70, 80],
                tension: 0.1
                }
            ]
        },
        options: {
            responsive: true,
            maintainAspectRatio: false
        }
    }
  },
  mounted () {
    this.renderChart(this.chartdata, this.options)
  }
}
</script>