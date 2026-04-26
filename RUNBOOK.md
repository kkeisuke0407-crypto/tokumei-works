# Runbook

## いま動いているもの

ローカルでは以下の自動生成が完了しています。

- note下書き: `dist/note_drafts/`
- 公開サイト: `site/`
- SNS投稿キュー: `dist/social_queue.csv`
- X共有URL: `dist/x_intents.json`

再生成する場合:

```powershell
python scripts/run_all.py
```

## 本番開始の順番

1. `dist/note_drafts/starter-kit.md` をnoteに貼り付けて有料記事として公開
2. 公開URLを `data/products.json` の `starter-kit.note_url` に入れる
3. `python scripts/run_all.py` を再実行
4. GitHubへpushしてGitHub Pagesを公開
5. 公開URLを `config/brand.json` の `site_url` に入れる
6. `python scripts/run_all.py` を再実行
7. A8.net、もしも、afb、楽天にGitHub Pages URLを媒体登録
8. 提携できた案件だけ `config/affiliate_links.json` に入れる
9. `dist/social_queue.csv` からSNS投稿を予約
10. 週1回、売れたテーマを増補する

## GitHub Actionsで全自動化

GitHub Pages公開後は、`.github/workflows/auto-build.yml` が毎日1回動きます。

手動実行:

1. GitHubのリポジトリを開く
2. Actionsタブ
3. `Auto Build Monetization Site`
4. `Run workflow`

定期実行では、サイト、note下書き、SNSキューが再生成されます。

## 触るファイル

- 商品を増やす: `data/products.json`
- ブランド名やURLを変える: `config/brand.json`
- 禁止表現を増やす: `config/rules.json`
- ASPリンクを入れる: `config/affiliate_links.json`

## 最初の14日間

- まず `starter-kit` だけ公開する
- Xは1日1から3投稿
- Instagramは週3投稿
- YouTube Shortsは週2本
- 1件売れたら `starter-kit` を増補
- 売れなければタイトルと無料部分を変える

