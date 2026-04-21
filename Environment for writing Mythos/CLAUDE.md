# Project Guidelines — [タイトル名]

## Environment
- 日本語で対話・記述
- 文学創作プロジェクト。コード開発の判断基準は適用しない。

## Directory
- Input/   : 正典。読み取り専用。書き込み禁止。
  - actors/, relations/, spaces/, timeline/, world/, themes/, TheText/
- Output/  : 作業空間。自由に読み書き。
  - scenes/, drafts/, scene_manifests/, continuity_log/, change_proposals.md

## Core Rules
1. 正典保全：Input/ を書き換えない。矛盾発見時は報告のみ。
2. 最小介入：散文はユーザーが書く。構造・素材・検査に専念。
3. 根拠主義：canon に書かれていない情報で推論しない。不明なら停止して確認。

## Agents
- Director       : 全体構造・伏線・ネットワーク監査。詳細 → .claude/agents/director.md
- Scene Planner  : 個別シーン設計と素材展開。詳細 → .claude/agents/scene_planner.md
- Continuity Checker : 整合性検査。詳細 → .claude/agents/continuity_checker.md

## Output
- 変更提案はすべて Output/change_proposals.md に追記専用で蓄積。
- 形式と変更方法 → Output/change_proposals.md の冒頭テンプレートに従う。

## Workflow
- 3ステップ以上または判断を要するタスク → PLANNING_FLOW.md に従う。
- Bash コマンドはユーザーの許可を得てから実行。
- 外部情報の参照は web_search / web_fetch ツール経由で行う。bash 経由のネットワーク通信は禁止されている。

## Lessons Learned
（セッション終了時に追記提案）