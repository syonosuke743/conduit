# 共通仕様

Article APIにおけるエンドポイントのドメイン名、リクエストが成功・失敗した際のレスポンス、レート制限などの共通仕様です。

# ドメイン名　http://127.0.0.1:3000/api/v1/articles
エンドポイント<br>


・記事を取得する<br>

・記事を作成する<br>

・記事を更新する<br>

・記事を削除する


# レート制限　なし


# ステータスコード
APIコールの後で、以下のHTTPステータスコードが返されます。ステータスコードの説明は、特に断りがない限り、HTTP status code specification (opens new window)に準拠しています。<br>

200 OK	...リクエストが成功しました。<br>

400 Bad Request ...	リクエストに問題があります。<br>

401 Unauthorized ...	有効なチャネルアクセストークンが指定されていません。<br>

403 Forbidden ...	リソースにアクセスする権限がありません。ご契約中のプランやアカウントに付与されている権限を確認してください。<br>

404 Not Found ...	記事情報を取得できませんでした。次のような理由が考えられます。<br>
　・対象の記事IDが存在していない<br>
 
409 Conflict	... 同じリトライキーを持つAPIリクエストがすでに受理されています。詳しくは、「失敗したAPIリクエストを再試行する」を参照してください。<br>

410 Gone	... 利用できなくなったリソースにアクセスしています。<br>

413 Payload Too Large ...	リクエストのサイズが上限を超えています。リクエストのサイズ小さくしてリクエストしなおしてください。<br>

415 Unsupported Media Type	... アップロードしようとしたファイルのメディア形式はサポートされていません。<br>

500 Internal Server Error	... 内部サーバーのエラーです。


# エラーレスポンス
エラー発生時は、以下のJSONデータを含むレスポンスボディが返されます。<br>

```json: {status: 'ERROR',  data: article.errors }```<br>
```json: { status: 'ERROR', message: 'Not updated', data: @article.errors }```
