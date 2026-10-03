これをパソコンでやってほしい
① Supabase（データベース）

	1.	https://supabase.com/ で無料プロジェクトを作成
	2.	「SQL Editor」で、ファイル冒頭に書いてあるSQL（テーブル作成＋公開ポリシー）を実行
	3.	「Project Settings」→「API」の「Project URL」と「anon public」キーを、ファイル冒頭の SAKAI_SUPABASE_CONFIG に貼る


② Cloudflare R2 + Worker（写真・動画の保存）
R2はFirebase Storageと違い、ブラウザから直接安全にアップロードする仕組みがないため、簡単な仲介役（Cloudflare Worker）を1つ用意する必要があります。

	1.	https://dash.cloudflare.com/ で無料アカウント作成、「R2」でバケットを1つ作成し、パブリックアクセスを有効化
	2.	「Workers」で新規作成し、ファイル冒頭に書いてあるコードをそのまま貼り付けてデプロイ
	3.	Workerの設定でR2バケットを紐付け、公開URLを環境変数に設定
	4.	発行されたWorkerのURLを、ファイル冒頭の SAKAI_R2_CONFIG に貼り付け