# tech-news

一次資料へのリンクを付けた、日本語の日次技術キャッチアップを作るAgent Skillです。Claude CodeとCodexで同じ `SKILL.md` を使えます。

## 内容

- 原則として当日07:00 JSTまでの24〜48時間を調査
- 一般技術、AIエージェント、セキュリティ、クラウド、Go・Linux・ネットワーク・OSSを整理
- What / Why / How、コミュニティ動向、深掘り、今日の結論を約20分の読み物に構成
- 過去号があれば重複を確認。取得できない場合は明記して続行
- 検証できた記事数に合わせて分量を調整し、事実と推論を区別

実行環境にWeb検索・ページ取得機能とその利用権限が必要です。特定のMCPや有料サービスは必須ではありません。Webを利用できない場合はその制限を明示し、提供された資料に基づくレポートに切り替えます。

## インストール

リポジトリを取得します（同名ディレクトリが既にあれば既存のものを使ってください）。

```sh
git clone https://github.com/takuto-san/tech-news.git
cd tech-news
```

下のコマンドはmacOS / Linux向けです。既存の同名スキルがある場合は上書きせずに停止します。更新時は差分を確認してから置き換えてください。

### Claude Code

```sh
mkdir -p "$HOME/.claude/skills"
if [ -e "$HOME/.claude/skills/tech-news" ] || [ -L "$HOME/.claude/skills/tech-news" ]; then
  echo '既存スキルがあります。差分を確認してください。'
else
  cp -R skills/tech-news "$HOME/.claude/skills/tech-news"
fi
```

新しいClaude Codeセッションで実行します。

```text
/tech-news 今日の技術キャッチアップを日本語で。過去号は提供していません。
```

### Codex

```sh
mkdir -p "$HOME/.agents/skills"
if [ -e "$HOME/.agents/skills/tech-news" ] || [ -L "$HOME/.agents/skills/tech-news" ]; then
  echo '既存スキルがあります。差分を確認してください。'
else
  cp -R skills/tech-news "$HOME/.agents/skills/tech-news"
fi
```

新しいCodexセッションで実行します。

```text
$tech-news 今日の技術キャッチアップを日本語で。過去号は提供していません。
```

プロジェクト単位で使う場合は、同じフォルダを対象リポジトリの `.claude/skills/` または `.agents/skills/` に置きます。重複登録を避け、個人用・プロジェクト用のどちらかを選んでください。Windowsでは同じ配置先へフォルダを手動コピーできます。

## 使い方の例

```text
2026-11-25の07:00 JST時点で。AIエージェントとセキュリティを重視。
過去号はこの会話に添付したMarkdownを参照して。
```

調査対象日、基準時刻、関心分野、過去号の場所を指定できます。未指定では当日・07:00 JSTです。07:00より前に実行した場合は、実際の調査時刻を基準とした暫定版になります。

レポートは実行中の会話に全文を返します。ファイル保存は明示的に依頼してください。自動スケジュールやSNS投稿、クラウドチャットの作成・改名は行いません。

## 移植時の変更

元のChatGPT Work向け指示から、特定プロジェクトと `MM.DD` 形式のチャット名の必須条件、専用チャットツールへの依存を除きました。調査基準と記事構成を維持し、過去号・Webアクセスがない場合、早朝の暫定版、記事不足時の扱いを明確にしています。週次振り返りやブックマーク整理は対象外です。

配置・起動方法の公式資料: [Claude Code Skills](https://code.claude.com/docs/en/skills)、[Codex Skills](https://developers.openai.com/codex/skills)。
