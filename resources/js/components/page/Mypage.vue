<template>
  <div>
    <main>
      <div class="container">
        <article class="col-md-8 col-xs-12">
          <section class="article-section">
            <h2 class="mypage-h2">
              <img class="mypage__logo" src="/images/answer.png" />マイページ
            </h2>
            <h3 class="mypage-h3"
              v-if="changeCorrectRatioData.length !== 0"
            >直近{{changeCorrectRatioData.percentage_correct_answer.length }}回の正解率推移</h3>
            <line-chart :chartData="lineChartData" ref="chart" style="height: 600px; width: 600px; margin:0 auto;"></line-chart>
          </section>
        </article>
      </div>
    </main>
  </div>
</template>

<script>
import LineChart from "../module/LineChart";
export default {
  components: {
    LineChart
  },
  data() {
    return {
      changeCorrectRatioData: [],
      lineChartData: {}
    };
  },
  mounted() {
    this.$http.get("/api/mypage").then(response => {
      this.changeCorrectRatioData = response.data;
      this.lineChartData = Object.assign({}, this.lineChartData, {
        labels: this.changeCorrectRatioData.created_at,
        datasets: [
          {
            label: ["最高得点率"],
            backgroundColor: "rgba(0, 170, 248, 0.47)",
            borderColor: "rgba(0, 170, 248, 1)",
            data: this.changeCorrectRatioData.percentage_correct_answer
          }
        ]
      });
      this.$nextTick(() => {
        this.$refs.chart.renderLineChart();
      });
    });
  }
};
</script>