## 制作の背景
自分の所属するゲームコミニティの待ち時間(対戦相手検索中など)を有効活用出来たらいいなと思い、手軽に遊べるクイズアプリを作りました。

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
①上記のURLをクリックしたら挑戦したいジャンルを選択してください(選択されたジャンルの合計問題数が10問以下の場合はTOPページに戻ります)
<br>
②出題開始をクリックするとクイズが始まります。
<br>
<img width="500" height="300" alt="choice" src="https://user-images.githubusercontent.com/61533662/81473001-c76e3800-9236-11ea-9d57-c5e481fd9b6a.png">
<br>
③ページが以降したら1~4正しいと思う選択肢をクリックすると正解が発表されます。画像下のボタンをクリックすると次の問題に移ります。
<br>
<img width="500" height="300" alt="quiz" src="https://user-images.githubusercontent.com/61533662/81472840-609c4f00-9235-11ea-918e-75d49f13f105.png">
<br>
<br>
④問題10問解き終わった後に結果が発表されます。
<br>
<img width="300" height="300" alt="result" src="https://user-images.githubusercontent.com/61533662/81472869-8b86a300-9235-11ea-9188-878b40ab686b.png">
<br>
<br>
⑤ログインした状態で2回(20問)以上クイズを解くとトップページのマイページから正解率推移を確認する事が出来ます。
<br>
<img width="300" height="300" alt="graph" src="https://user-images.githubusercontent.com/61533662/81472884-a35e2700-9235-11ea-92da-87315ecc0683.png">
<br>
<br>

## 使用技術

<h4>バックエンド</h4>
<ul>
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
<h4>Laravel-Adminでサイトの下記情報を新規作成、編集、削除できます</h4>
<ul>
<li>問題文</li>
<li>選択肢</li>
<li>正解の択</li>
<li>クイズカテゴリー</li>
<li>ユーザー情報</li>
</ul>

<img width="500" height="300" alt="admin" src="https://user-images.githubusercontent.com/61533662/79821350-83231100-83c9-11ea-8bad-d66613352d77.png">

## ER図
<img width="500" alt="500" src="https://user-images.githubusercontent.com/61533662/79824281-de0c3680-83d0-11ea-917d-491bef7cc993.png">


## デモ画面
![demo](https://user-images.githubusercontent.com/61533662/79710832-21976f80-8301-11ea-882f-449f81732bf3.gif)

## 今後の課題
テストコードの記載
<br>
ユーザー登録時画像も投稿できるようにする

