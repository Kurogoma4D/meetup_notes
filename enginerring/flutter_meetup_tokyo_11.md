# introduction
## Zoeyさん & Martinさん
Product Manager & Marketing Manager
- Flutterの紹介
  - Flutterの成り立ち，仕組み
  - 宣言的レイアウト
  - 端末でもIDEでも開発できるよ
  - Dart
- 圧倒的成長
  - 日本でもツール使用率が250%増加
  - AlibabaのPV
  - Flutter Create（コンテスト）

# LT
## Flutter製アプリのアクセシビリティ対応（音声読み上げ編)
なのなの氏
- 多くの人にアプリを使ってもらうには→アクセシビリティ
  - Android Developerのサイトでも言及されている
  - Android iOS両方でおおよそ同じサポートが可能
  - 今回は音声読み上げについて
  - AndroidではTalkbackという名前

### 読み上げ機能
- そもそもFlutter製アプリは対応してるのか？
  - 対応はしている
- しかし，自分で読み上げ方を制御したいこともある
- 画像の場合
  - `semanticLabel` にStringを設定するだけ
- テキストの場合
  - 読み上げさせたくないやつは， `Semantics` ウィジェットを使う
- `Semantics` の `sortKey` プロパティを使うことで，読み上げの順番を変えられる
- 好きなタイミングで
  - `SemanticsService.announce('')`
- `MediaQuery` で音声読み上げがオンかどうかわかる

## Getting Screenshots in Flutter
macs_6氏
Its all widgetsに個人開発アプリを登録してる

- スクリーンショットをいい感じの状態で撮りたい
  - ストアに乗せる画像
  - Golden file testing

### Golden files
- `matchesGoldenFile`
  - スクショ画像と現在のレンダリング結果を見るテスト
  - `flutter test --update-goldens` でファイルの更新もやってくれる

### ストア画像
- `sample_page.dart`
  - コードの下にコメントを書いて `flutter drive` コマンドを叩くと，カタログ用のHTMLやスクショを生成できる

## Mobile Recap from DroidconKE 2019
Kenichi Kambara氏

### .droidcon KE
- droidconのケニア開催
- 登壇してきました
  - FlutterでのUI記述について
  - widgetのボイラープレート紹介(stfulとか)
- 他のセッション
  - ケニアはスワヒリ語と英語だが，アプリダウンロードはスワヒリ語のほうが伸びる
  - 課金に対応してない国もあるので，別のビジネスモデルが必要
  - アフリカではAndroid使用率97%だったり

## Release Flutter App （Video On Demand）
tanaka氏  
Video Market Corp.

### videomarketリリースしました
- 現在iOSのみ
- VODサービス
- iPhone，iPadでジェスチャーコントロールも一部対応
- Apple TVでも再生できます
- シークバーでコントロール可能
- ジェスチャーコントロール
  - 画面の明るさ調整
  - 音量調整
- バックエンドはGCP
- クライアント側でPlatform channelを活用
  - 再生部分，課金部分
  - iOS開発の資産があったので活用しました
- TV appとの連携
  - TV appから再生ボタンを押すと，Deep linkでvideomarketに飛ぶ

## Flutterを仕事で使いたい
nemui_fujiu氏

- 仕事で使うには，会社との合意形成が必要
- 信頼関係が大事
- 「これから新しい技術使ってください！」
  - 使ってる事例が多ければ多いほど採用されやすい
- 自身の知見がまだ浅い
  - 勉強します
  - 公式サイトをひたすら読む
    - 英語だけど，Google翻訳が超便利なので読める
  - 他人に対してアウトプット
    - 日本語の解説サイトを自作
- 人の意見も聞いておく
  - Flutter Meetup Tokyo
- さらなるアウトプット
  - 解説本の執筆してみました
    - 技術書展で本出します
- ここまで9ヶ月
  - いま「完全に理解した」レベル
  - 「何もわからん」まで行きたい
  - まだアプリを作ってリリースしてない！
  - 感想「Flutterを仕事で使いたい」
- 同人誌は期限付きなので，集中して勉強できました
- 楽しいからといって，いじくり回してるだけじゃ仕事になりません
- 次のアプリはフルリニューアルで導入