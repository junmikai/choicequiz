## 制作の背景
自分の所属するゲームのコミニティの待ち時間(対戦相手検索中など)を有効活用出来たらいいなと思い、手軽に遊べるクイズアプリを作りました。

## 本番環境 URL

https://choicequiz.herokuapp.com/
<br>
メールアドレス：anser@gmail.com
<br>
パスワード：07230723
<br>
(ログインしなくてもクイズに挑戦出来ます)
<br>

## 使用方法
上記のURLをクリックしたら画面中央の出題開始をクリックするとクイズが始まります。
<br>
<img width="400" height="300" alt="toppage" src="https://user-images.githubusercontent.com/61533662/79689539-7f3fa380-8290-11ea-84d3-8513ef152c54.png">
<br>
クイズが始まったら1~4正しいと思う選択肢をクリックすると正解が発表されます。画像下のボタンをクリックすると次の問題に移ります。
<br>
<img width="400" height="300" alt="quiz" src="https://user-images.githubusercontent.com/61533662/79705413-98783c80-82f0-11ea-80cf-df85021d0a1d.png">
<br>
問題10問解き終わった後に結果が発表されます。
<br>
<img width="400" height="300" alt="result" src="https://user-images.githubusercontent.com/61533662/79705524-f9a01000-82f0-11ea-9875-23b6c7f331a6.png">
<br>
ログインした状態で2回(20問)以上クイズを解くとトップページのマイページから正解率推移を確認する事が出来ます。
<br>
<img width="400" height="300" alt="graph" src="https://user-images.githubusercontent.com/61533662/79705781-d9248580-82f1-11ea-9157-3786ddcf7a86.png">
<br>

## 使用技術

<h4>バックエンド</h4>
<ul>
<li>php 7.3.16</li>

<li>php 7.3.16</li>
<li>Larave l6.8</li>
<li>axios 0.19.2</li>
<li>vee-validate 3.2.5</li>
<li>laravel-admin 1.7</li>
<li>Laravel 5 Very Basic Auth</li>
</ul>

<h4>フロントエンド</h4>
<ul>
<li>Sass</li>
<li>JavaScript</li>
<li>Bootstrap3</li>
<li>vue 2.6.11 </li>
<li>chart.js 2.9.3</li>
<li>vue-chartjs 3.5.0</li>
</ul>

<h4>インフラ・開発環境等</h4>
<ul>
<li>Composer 1.10.5</li>
<li>heroku</li>
</ul>

## 機能一覧
<h4>下記のページはAPI連携による非同期通信を実施</h4>
<ul>
<li>ホーム画面のカテゴリー選択</li>
<li>ホーム画面からクイズ画面に以降</li>
<li>クイズ出題画面</li>
</ul>
<h4>ユーザー登録機能</h4>
<ul>
<li>CSRF保護でアプリケーションを操作していないユーザーの攻撃を対策</li>
<li>登録済メールアドレスとパスワードによるログイン方式</li>
<li>パスワードは8文字以上に制限</li>
</ul>
<h4>ランキング機能</h4>
<ul>
<li>Objectのデータを追加</li>
<li>登録済メールアドレスとパスワードによるログイン方式</li>
<li>パスワードは8文字以上に制限</li>
</ul>

## 管理画面
<h4>Laravel-Adminでサイトの情報を管理</h4>
<ul>
<li>問題文</li>
<li>選択肢</li>
<li>正解の択</li>
<li>クイズカテゴリー</li>
<li>ユーザー情報</li>
<li>Basic認証によるセキュリティ強化</li>
</ul>


## デモ画面
![demo](https://user-images.githubusercontent.com/61533662/79710832-21976f80-8301-11ea-882f-449f81732bf3.gif)

## 今後の課題
テストコードの記載
<br>
ユーザー登録時画像も投稿できるようにする

