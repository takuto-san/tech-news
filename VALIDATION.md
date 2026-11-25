# 検証結果

検証日: 2026-11-25（JST）

| 対象 | 結果 |
| --- | --- |
| SKILL.mdの構造 | skill-creatorの `quick_validate.py` で正常。name / descriptionを持つ共通YAML frontmatter |
| READMEのClaude Code配置手順 | 一時ディレクトリで実行し、コピー元とのバイト一致を確認 |
| READMEのCodex配置手順 | 一時ディレクトリで実行し、コピー元とのバイト一致を確認 |
| インストールの再実行 | 両手順とも既存フォルダを保持し、上書きせずに終了 |
| Codex CLI 0.153.4 | 一時プロジェクトの `.agents/skills/` に配置し、`$daily-tech-catchup` でスモークテスト通過 |
| Claude Code 2.1.261 | `.claude/skills/` に配置して `/daily-tech-catchup` を試行したが、未ログインで停止。モデルによるスキル認識・レポート生成は未検証 |
| 配置・起動方法 | 両製品の公式Skills資料と照合 |

Codexのスモークテストでは、Web検索・取得を禁止し、記事資料も過去号も与えずに最初の返答を要求しました。今日のニュースを生成せず、検証できない理由と過去号の未確認を明示し、公開日・出典URL付きの資料提供を案内する応答を確認しました。読み取り専用・一時セッションで実施しています。起動時に無関係のTodoist MCP認証エラーも出ましたが、スキルへの応答は正常に完了しました。このスキルはTodoistを必要としません。

実ニュースの全件調査、複数ターンでの過去号照合、Claude Codeでの認証後の実行、Windows上の実行は今回の検証対象外です。これらの動作確認済みとは主張しません。

## 手元での確認

1. READMEに沿ってスキルを配置し、認証済みの新しいCLIセッションを開く。
2. Claude Codeでは `/daily-tech-catchup`、Codexでは `$daily-tech-catchup` を付けて、Web利用禁止・資料なしで最初の返答を要求する。架空ニュースを生成せず、制限を明示することを確認する。
3. Webを利用できる環境で対象日と過去号の有無を指定して実行する。出典本文、基準時刻、実際の記事数、重複の扱いを確認する。

公式資料: [Claude Code Skills](https://code.claude.com/docs/en/skills)、[Codex Skills](https://developers.openai.com/codex/skills)。
