# Design

1. Runner
  * CLI optionから要求を受け取ってparseする
  * シナリオを選択し引数をぶちこんで起動する(最大走行時間も与えること)
  * シナリオから結果オブジェクトを受け取ってJSONにして出力する
  * http clientの管理もやる？
2. Senario
  * 引数リストに対して何をやるかをひたすら書いてある
  * ループを表現できるようにすること
  * いくつか異なるパターンの行動を入れておく
  * 複数のセッションをわたり歩いて一連のリクエストを投げられるようにしておく
  * シナリオをキックできるシナリオを作る
  * 並列実行中の一連のリクエストおよびシナリオの状態を監視する
  * チェッカを生成して保持する
  * リクエストが完了したら
    * チェッカを呼ぶ (コンテンツのチェックが必要なくてもHTTPステータスやレスポンスタイムを戻したりするためのものを作る)
    * チェッカの結果をResultにマージする
    * シナリオ完了条件までは、次のリクエストを積む
  * シナリオが完了したら
    * シナリオ間のResultをマージする
    * 次のシナリオをキックする(かRunnerに返す)
  * リクエスト数とその結果およびレスポンスタイム統計、チェッカ結果などをまとめてRunnerに返す (そのためのクラスがいる？)
3. Request
  * http clientを受け取って非同期リクエストを投げる
  * 結果が返ったら一度シナリオに戻す -> シナリオが次のリクエストを積む？
