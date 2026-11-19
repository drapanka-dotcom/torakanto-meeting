# トラ関東会 目論見書

トラ関東会の目論見書を管理するリポジトリです。

> ⚠️ **このリポジトリは関係者限り・外部公開厳禁です。**
> Privateリポジトリのまま運用し、URL・内容の外部転載／共有は禁止です。
> **GitHub Pages等での公開は絶対に行わないでください。**

## ファイル構成

| ファイル | 役割 |
|---|---|
| `目論見書.md` | **原本**。文言の修正はこのファイルを編集する |
| `目論見書.html` | 配布用HTML。Markdownの変更を反映して更新する |
| `template.html` | Pandoc用HTMLテンプレート（任意で使用） |
| `style.css` | HTMLのスタイル |
| `defaults.yaml` | Pandoc用設定ファイル（任意で使用） |

## 更新フロー（基本運用）

1. `目論見書.md` を編集する
2. 変更内容をAI（DeepSeek）に渡し、`目論見書.html` を更新してもらう
3. 両ファイルをコミットする
4. 必要に応じてHTMLをPDF化して配布する

### AIへの依頼テンプレート

```text
【旧Markdown】
（変更前の 目論見書.md）

【新Markdown】
（変更後の 目論見書.md）

【版数】
v1.4 に上げる ／ 据え置き

【更新履歴の追記文言】
（なければ「差分から要約して」）

【その他要望】
（例：注意ボックスは維持、など）
```

## 版数管理ルール

- 版数は `v1.0` から開始し、内容変更ごとに `v1.1`, `v1.2` … と上げる
- **Markdown冒頭の `updated:`** と、**本文の更新履歴表**の両方を更新する
- コミットメッセージは `v1.4 注意事項の古語修正` のように **版数＋変更内容** を書く

## Pandocで変換する場合（任意）

Pandocがインストールされていれば、MarkdownからHTMLを自動生成できます。

```bash
pandoc 目論見書.md -d defaults.yaml -o 目論見書.html
```

PDF化：

```bash
pandoc 目論見書.md -d defaults.yaml --pdf-engine=wkhtmltopdf -o 目論見書.pdf
```

> 注意：Pandoc変換では注意ボックス（`.note.caution`）が通常のリストになります。
> デザインを維持したい場合はAIに依頼する運用（上記「更新フロー」）を推奨します。

## 公開禁止事項

- GitHub Pages / Netlify / Vercel 等への公開
- リポジトリのPublic化
- オープンチャットURLの外部共有
- PDFの外部転載

## 共同編集

運営メンバーを追加する場合：
1. リポジトリの「Settings」→「Collaborators」
2. 「Add people」でGitHubアカウントを招待
3. **Privateのまま**共同編集可能
