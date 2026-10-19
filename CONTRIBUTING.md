# CONTRIBUTING

このリポジトリに自分の紹介サイトを提出するためのルールと手順をまとめます。
教員と学生の両方がスムーズに作業できるように、必ずこの手順に従ってください。

---

## 目的
各学生が作成した自己紹介ウェブページを `students/` 以下に集約し、トップページ `index.html` には各学生のページへのリンクを掲載します。

---

## ルール（必須）
1. 各学生のサイトは `students/<github-username>/index.html` に配置してください。
   - 例えば GitHub ユーザ名が `alice` なら `students/alice/index.html`。
   - 画像や CSS は `students/<github-username>/assets/` に入れて相対パスで参照してください。
2. ルートの `index.html`（クラス一覧）へのリンクは相対パスで追加してください。
   - 例: `<li><a href="students/alice/index.html" target="_blank" rel="noopener">Alice</a></li>`
3. 外部の JavaScript を自由に埋め込むことは禁止します（XSS や悪意あるコード防止のため）。
   - 例外が必要な場合は事前に教員に相談してください。
4. 公序良俗に反する内容や個人情報の過剰な公開は禁止です。
5. 画像の著作権に注意してください。自作の画像か、ライセンス確認済みの素材のみ使用してください。

---

## 提出ワークフロー（推奨）
以下はフォークしてから PR を作る一般的な手順（コマンド例）です。

1. リポジトリを Fork（GitHub 上で右上の Fork ボタン）。
2. 自分のフォークをローカルにクローン:

```bash
git clone https://github.com/<your-username>/Class2026.git
cd Class2026
```

3. ブランチを作る（ブランチ名ルール）:

```bash
git switch -c add-site-<姓>-<学籍番号>
# 例: add-site-suzuki-20260123
```

4. 自分のディレクトリを作り、ファイルを追加:

```bash
mkdir -p students/<your-github-username>/assets
# 自己紹介ページを作成
# students/<your-github-username>/index.html を追加
# 画像や CSS は students/<your-github-username>/assets/ に配置
```

5. ルートの `index.html` に自分のリンクを追加（上の相対パス例を参照）。
6. 変更をコミットしてプッシュ:

```bash
git add students/<your-github-username> index.html
git commit -m "Add site for <Your Name>"
git push origin add-site-<姓>-<学籍番号>
```

7. GitHub でフォークのブランチからオリジナル（upstream）リポジトリへ Pull Request を作成。
   - PR のタイトル例: `Add site: <Your Name>`
   - PR の説明に自分のページのURL（リポジトリ内の相対パス）と確認手順を書いてください。

---

## ブランチ・ファイル命名規則（推奨）
- ブランチ: `add-site-<姓>-<学籍番号>`
- ページ: `students/<github-username>/index.html`
- アセット: `students/<github-username>/assets/...`

---

## PR チェックリスト（PR に必ず含めること）
- [ ] `students/<github-username>/index.html` が存在する
- [ ] ルート `index.html` にリンクを追加した（相対パス）
- [ ] ブラウザでローカル確認済み（表示・画像・リンク）
- [ ] 外部スクリプトを埋め込んでいない
- [ ] 画像等のライセンスは問題ない

---

## 教員のレビュー基準（簡潔）
- 表示崩れやリンク切れがないか確認します。
- 危険なスクリプトや外部埋め込みがないかを確認します。
- 問題なければマージして公開します。

---

## ローカルでの確認方法
- 単純にブラウザで `students/<your>/index.html` を開いて確認できます。
- ローカルで簡易 HTTP サーバを立てる場合（例: Python）:

```bash
# Python 3 の場合
python -m http.server 8000
# ブラウザで http://localhost:8000/ を開く
```

---

## オプション（自動化案）
- GitHub Actions を導入して、PR ごとにリンクチェッカーや HTML Validator を走らせると便利です。
- GitHub Pages を有効にすれば、マージ後に自動的に公開できます（`gh-pages` または `main` ブランチで Pages を設定）。

---

## トラブルシューティング
- もし `git push` で権限エラーが出る場合は、Fork を使っているか、push 先のリモートが自分の fork になっているか確認してください。
- `index.html` の競合が起きたら、ローカルで最新の upstream を fetch して rebase してください。

---

## 連絡先
問題がある場合や例外の相談は授業用の Issue を立てるか、担当教員まで連絡してください。

---

## 付録：index.html に追加するリンクの例
```html
<li><a href="students/alice/index.html" target="_blank" rel="noopener">Alice</a></li>
```

以上。提出ルールのドラフトです。疑問・変更したい点があれば教員側ルールに合わせて文言を調整します。
