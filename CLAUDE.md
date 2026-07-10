# mercilint

コードを容赦なく煽る(roast)が、全ツッコミが実際の修正提案に対応しているClaude Codeレビュースキル。「ネタの皮を被った実用スキル」。

要件・計画の詳細は docs/REQUIREMENTS.md を参照。

## 技術スタック
- Markdownのみ(SKILL.md + README)。コード実装なし、ビルド・デプロイなし
- 配布形態: Claude Codeスキル(GitHubからインストール)

## ディレクトリ構成
- `SKILL.md` — スキル本体(配布物)。ユーザーは `~/.claude/skills/roast/` にcloneして使う(コマンド名はディレクトリ名で決まるため)
- `README.md` — 英語の公開用README(配布物)
- `docs/` — 内部ドキュメント(日本語)。IDEA.md(壁打ち結果)、REQUIREMENTS.md(要件・マイルストーン)

## コマンド
ビルド・テストなし。動作確認は `ln -s $(pwd) ~/.claude/skills/roast` でリンクし(コマンド名はディレクトリ名で決まる)、実際のdiffがあるリポジトリで `/roast` を叩く

## 規約・注意点
- **ユーザー向け成果物(SKILL.md・README・roast文言)はすべて英語**。グローバル向けで日本語ローカライズはしない。docs/ 配下の内部ドキュメントは日本語でよい
- **roastには必ず修正提案とseverity(致命/高/中/低)を対応させる**。煽りだけのツッコミは仕様違反
- キャラは単一。口調・声のガイドラインはSKILL.md内に蒸留し、ブレさせない
- リポジトリはpublic化(M3)まではprivate前提。public化時にMITライセンスを付与
