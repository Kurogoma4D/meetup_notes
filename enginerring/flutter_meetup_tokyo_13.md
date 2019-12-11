# Supernova StudioでFlutter爆速開発の夢を見れるか？
片岡氏 データスタジアム株

## Supernova Studio
デザインをコードにするツール
Xd，Sketch → Supernova → Swift, Java, Kotlinなどにエクスポートできる
今年3月にFlutter Export対応

一定以上の規模の開発で，エンジニアがデザインを観ながらレイアウト，アニメーションのコーディングをするフェーズが大幅時間短縮できる

- Xdのオブジェクト一つ単位でコードを起こしてくれる
- 画面上で直接デザインの変更，反映も可能
- ナビゲーションも作れる

そのまま起動するとエラー…？

絶賛開発中みたい

今日あたりリリースされるバージョンでエクスポートに関する問題を大量に修正するよ！

# Flutterプラグインでdart:ffiを使ってみる
川崎氏 クミナス株

## ffi
foreign function interface
dart:ffiは，主にC言語の関数を呼び出す

機能
- Cの関数を呼び出す
- ポインタに直接書き込む機能
- ポインタを直接読み込む機能

Binding to native code using dart:ffi!

## 使ってみる
プラグインテンプレで作成 → ネイティブ側でファイルを足すだけ

- Androidでは吐かれた共有ライブラリ
- iOSではプロセスのモジュール

を読み込む形

Androidの場合，Gradleに絡ませないといけない
`CMakeLists.txt` にCのファイルを記述，これをGradleのビルド対象に含める

dar:ffiは簡単！

dart:ffi内のサンプルにもいくつか読み解くべきものがある
dart:ffiにない機能がffiパッケージで読める

関数インポート，ポインタ演算など

構造体はかなり大変…
dartのクラス管理ではなく，C側にメモリを確保する→ガベージコレクションの対象にならない（！）
あとネストもできない

# Flutter desktop embedding for Linux
kurun氏 ソニー SE

## とは
FlutterアプリがWin/mac/Linuxで作れますよ
発表から1年，まだ不安定

mac以外はデバッグモードのみで動く
macはyaml修正でプラグイン関係も行けるけど，それ以外はmakefileなどを修正しないといけない

## Linuxで動く仕組みを追ってみた
cppコードから，dart側のコードを呼びだし
runコマンドもしくはbuildコマンドを実行することで，pubspecに登録したプラグインのコードを生成
GUIはGtk

割と普通に動いたけど，まだプロダクションレベルではない

# Desktop向け業務アプリでFlutterを採用しようとした話
mi6ock氏 PST株

## 要件
- Xプラット
- C/C++呼び出し
- など

結果としてElectronが採用された
悔しいので話をします

## 魅力
- Material
- Hot Reload

プラグインが現状少ないけど，拡張できます

## Desktopに必要そうな機能
- キーボード入力 いける
- メニューバー
  - mac, Linuxのみ
- データ永続化
  - macはshared preference
  - sembast.dart
- ネットワーク接続 できる
- ファイル選択
  - file_chooser

# アプリ名を変更するプラグインを作った話
ダイスケ氏 フリーランス

## タイトルどおり

ビルドした時のアプリ名とアイコンを変えたい
info.plistとかを直接いじる説明しかない

公式のドキュメントが結構充実してるので，公式通りにやれば結構すんなりいけた
flutter_launcher_iconsとほぼ同じ作り

# Atomic DesignをFlutterでやってみた
つっちー氏 株hirundo

## Atomic Design
Widget の切り分け方として採用
うまくやれば再利用しやすいWidgetが作れそう

BLoCの設計

- Global BLoC
  - 認証処理など
- UI BLoC
  - そのた

Atoms, Molecules がUI側依存すると他のUIで扱いづらい

UI BLoC だとProviderの良さが活かしきれない
Atoms, Molecules の管理が大変

結論：再利用を諦める
Flutterの特徴である速度を取るため
Organismsレベルなら再利用を考えてもいいかも

# そのアプリ…文字サイズをデカくしてもUI崩れないですか？
岡部氏 株Tenxia

看護領域のネイティブアプリをリプレイスした

Flutterは文字サイズ調整が楽なのでトライしてみよう

スマホアプリってそもそも高齢者の利用が多くなっていく見立てなので，そこに対してもUXを考えなきゃいけないよね

OS側でテキストサイズを変更されると，エンジニアとしては考えることが増える

iOS版Twitterはアプリ内で文字サイズ変更ができる

Flutterではどうするか

TextScaleFactor
便利なプラグイン AutoSizeText
