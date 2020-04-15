JavaによるAkkaトレーニング第2回 

## アクターによる非同期処理

Akkaは非同期処理を実装するのに有用なツールキットです。
今回はAkkaのアクターを使った非同期処理を紹介し、3層アーキテクチャで用いたデータベース・トランザクションによる排他制御との違いを学びます。

- [次回のトレーニング: アクターとデータベースのシステム(イベント・ソーシング)](https://github.com/mvrck-inc/training-akka-java-3-persistence)

## 課題

この課題をこなすことがトレーニングのゴールです。課題を通じて手を動かすとともに、トレーナーと対話することで学びを促進することが狙いです。

- [課題提出トレーニングのポリシー](https://github.com/mvrck-inc/training-akka-java-1-preparation/blob/master/POLICIES.md)


## この課題で身につく能力

- akkaのアクターを使って素早く最小限のアプリケーションを作成できる
- 状態遷移図をもとにアクターの実装をソースコードに書き起こせる

### 事前準備:

MacBook前提。

- Mavenをインストールしてください
  - `brew install maven`

### 作業開始:

MacBook前提。

- TODO: アプリケーション図示 

- このレポジトリをgit cloneしてください
  - `git clone git@github.com:mvrck-inc/training-akka-java-2-actor.git`
- アプリケーションを走らせてください
  - `mvn compile`
  - `mvn exec:java -Dexec.mainClass=com.mycompany.app.Main`
- curlでデータを挿入してください
  - レスポンスを確認してください
  - アプリケーション側のログを確認してください
- wrk -t2 -c4 -d5s -s wrk-scripts/order.lua http://localhost:8080/orders
  - t2: 2 threads, c4: 4 http connections, d5: test duration is 5 seconds
  - クライアント側とサーバー側の実行結果を確認してください
- チケット(在庫)とオーダーの整合性を保つ[シーケンス図](https://plantuml.com/sequence-diagram)を[確認してください](../)
- チケット(在庫)とオーダーの[状態遷移図](https://plantuml.com/state-diagram)を[確認してください](../)
- それぞれの状態の詳細な状態遷移図を見てコマンド、遷移可能状態、副作用を[確認してください](../)
- 状態遷移「表」を[確認してください](../)
- ソースコードのコマンドを[確認してください](../)
- ソースコードの状態の定義を[確認してください](../)
- ガーディアンアクター以下親子関係のから樹形図を[確認してください](../)
- シーケンス図を複数アクターに拡大したものを[確認してください](../)
- 各アクターの実装を確認してください
  - [ガーディアン](../)
  - チケット在庫アクター[親](../)[子](../)
  - オーダーアクター[親](../)[子](../)
- akka-httpのセットアップを[確認してください](../)

### 発展的内容:

- 状態遷移図で売り切れ後のチケット追加販売を考えてください
- 状態遷移図でオーダーのキャンセルを考慮してください
- 状態遷移図でイベントの中止、払い戻しを考えてください
- 状態遷移図で先着と抽選の2通りを考えてください
- 状態遷移図で複数チケットの同時購入を考えてください
- 不正データのハンドリング、業務例外を考えてください
  - 不正なオーダーを弾いてください(年齢制限、不正なチケット種別の組み合わせ、などなど) 
  - 購入履歴と照らし合わせた不正な購入を防いでください
- asyncテストが必要となるテストケース例を考えてください
- コンサート以外に、スポーツや映画、入場券のみイベントを実現するテーブルを考えてください

## 説明

- [課題背景](./BACKGROUND.md)
- [課題提出方法](./SUBMIT.md)
- [課題手順の詳細](./DETAILES.md)

## 参考文献・資料

- https://plantuml.com/