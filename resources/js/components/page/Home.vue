<template>
  <div>
    <main>
      <div class="container">
        <article class="col-md-8 col-xs-12">
          <section class="home-quiz__introduction">
            <h2 class="home-quiz__introduction-h2">
              <img class="home-quiz__introduction-h2-logo" src="/images/top.png" />BusiChoiceとは？
            </h2>
            <transition appear name="slide-fade">
            <p v-if="show">ビジネスに関する4択問題をランダムに10問出題。1回3分で終わるから隙間時間で遊べます！
              <br>
              ログインしなくてもクイズに挑戦出来ます！
            </p>
            </transition>
          </section>
            <section class="home-quiz__setting">
            <h2 class="home-quiz__setting-h2">
              <img class="home-quiz__setting-h2-logo" src="/images/category.png" />出題設定
            </h2>
            <form>
              <label v-for="(cate, index) in category" :key="index">
                <input type="checkbox" v-model="categories" :value="cate.id" checked />
                {{cate.name}} 
              </label>
              <div class="allbtn">
                全項目チェック
                <button type="button" @click="checkAll">ON</button>
                <button type="button" @click="checkAllOff">OFF</button>
              </div>
              <button type="submit" class="btn-box btn-success" style="width:250px; height:75px;" @click.stop.prevent="goQuiz()">出題開始</button>
            </form>
          </section>
          <section class="home-quiz__introduction">
            <h2 class="home-quiz__introduction-h2">
              <img class="home-quiz__introduction-h2-logo" src="/images/finger.png" />遊び方
            </h2>
              <button class="btn-box btn-primary" v-on:click="show2 = !show2">遊び方はこちらをクリック</button>
              <transition name="bounce">
                 <p v-if="show2">
              ①上記の「出題設定」から挑みたいジャンルを選択したら「出題開始」ボタンを押します。
              <br>
              <br>
              ②ページが以降したら1~4正しいと思う選択肢をクリックすると正解が発表されます。画像下のボタンをクリックすると次の問題に移ります。
              <br>
              <img width="500" height="300" alt="quiz" src="https://user-images.githubusercontent.com/61533662/81472840-609c4f00-9235-11ea-918e-75d49f13f105.png">
              <br>
              <br>
              <br>
              ③問題10問解き終わった後に結果が発表されます。
              <br>
              <img width="300" height="300" alt="result" src="https://user-images.githubusercontent.com/61533662/81472869-8b86a300-9235-11ea-9188-878b40ab686b.png">
              <br>
              <br>
              <br>
              ④ログインした状態で2回(20問)以上クイズを解くとトップページのマイページから正解率推移を確認する事が出来ます。
              <br>
              <img width="300" height="300" alt="graph" src="https://user-images.githubusercontent.com/61533662/81472884-a35e2700-9235-11ea-92da-87315ecc0683.png">
              <br>
              <br>
              <br>
              </p>
              </transition>
          </section>
          <section class="home-quiz__ranking">
            <h2 class="home-quiz__ranking-h2">
              <img class="home-quiz__ranking-h2-logo" src="/images/ranking.png" />ランキング
            </h2>
                <button class="btn-box btn-primary" v-on:click='active02=!active02' v-bind:class='{active:active02}'>ランキングはこちらをクリック</button>
                <ul class="text">
                  <li class="serif" v-bind:class='{active:active02}'>
            <div>
              <label>
                <input class="ranking-radio" type="radio" v-model="rankingType" value="1" />総合
              </label>
              <label>
                <input class="ranking-radio" type="radio" v-model="rankingType" value="2" />今月
              </label>
              <label>
                <input class="ranking-radio" type="radio" v-model="rankingType" value="3" />今週
              </label>
            </div>
            <div class="home_quiz__ranking-chart" style="height: 700px; width: 700px; margin:0 auto;">
              <bar-chart :chartData="total" ref="totalChart" v-show="rankingType === '1'"></bar-chart>
              <bar-chart :chartData="month" ref="monthChart" v-show="rankingType === '2'"></bar-chart>
              <bar-chart :chartData="week" ref="weekChart" v-show="rankingType === '3'"></bar-chart>
            </div> 
                </li>
              </ul>    
          </section>
          <section class="home__notice">
            <h2 class="home__notice-h2">
              <img class="home__notice-h2-logo" src="/images/speaker.png" />お知らせ情報
            </h2>
            <dl v-for="(info, index) in information" :key="index">
              <dt>{{info.created_at}}</dt>
              <dd>{{info.information}}</dd>
            </dl>
          </section>
        </article>
      </div>
      <notifications />
    </main>
  </div>
</template>

<script>
import BarChart from "../module/BarChart";

export default {
  components: {
    BarChart
  },
  data() {
    return {
      categories: [1,2,3,4,5,6],
      information: [],
      category: [],
      rankingAlldata: {},
      week: {},
      month: {},
      total: {},
      rankingType: "1",
      selectAll: false,
      active01: false,
      active02: false,
      show:true,
      show2: false,
    };
  },
  mounted() {
    this.$http.get("/api/category").then(response => {
      this.category = response.data;
    });
    this.$http.get("/api/information").then(response => {
      this.information = response.data;
    });
    this.$http.get("/api/ranking").then(response => {
      this.rankingAlldata = response.data;
      this.setRanking();
    });
    const referrer = document.referrer;
    if (referrer.indexOf("/login") !== -1) {
      this.displayNotification("ログインしました", "info");
      this.resetReferrer();
    } else if (referrer.indexOf("/register") !== -1) {
      this.displayNotification("会員登録しました", "success");
      this.resetReferrer();
    }
  },
  methods: {
    checkAll() {
      let val = [];
      this.category.forEach(element => {
        val.push(element.id);
      });
      this.categories = val;
    },
    checkAllOff() {
      this.categories = [];
    },
    goQuiz() {
      this.$router.push("/quiz?categories=" + this.categories);
    },
    setRanking() {
      this.week = Object.assign({}, this.week, {
        labels: this.rankingAlldata.weekRankingData.name,
        datasets: [
          {
            label: ["最高得点率"],
            backgroundColor: "rgba(0, 170, 248, 0.47)",
            data: this.rankingAlldata.weekRankingData.percentage_correct_answer
          }
        ]
      });
      this.month = Object.assign({}, this.month, {
        labels: this.rankingAlldata.monthRankingData.name,
        datasets: [
          {
            label: ["最高得点率"],
            backgroundColor: "rgba(0, 170, 248, 0.47)",
            data: this.rankingAlldata.monthRankingData.percentage_correct_answer
          }
        ]
      });
      this.total = Object.assign({}, this.total, {
        labels: this.rankingAlldata.totalRankingData.name,
        datasets: [
          {
            label: ["最高得点率"],
            backgroundColor: "rgba(0, 170, 248, 0.47)",
            data: this.rankingAlldata.totalRankingData.percentage_correct_answer
          }
        ]
      });
      this.$nextTick(() => {
        this.$refs.totalChart.renderBarChart();
        this.$refs.monthChart.renderBarChart();
        this.$refs.weekChart.renderBarChart();
      });
    },
    resetReferrer() {
      Object.defineProperty(document, "referrer", {
        value: location.href
      });
    },
    displayNotification(text, type) {
      this.$notify({
        title: "お知らせ",
        text: text,
        type: type
      });
    }
  }
};
</script>