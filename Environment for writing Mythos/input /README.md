# Input/ ディレクトリ構成

このディレクトリは作品の**正典（Canon）**である。
Claude Code は読み取り専用で参照し、書き込みは行わない。
すべての変更提案は `Output/change_proposals.md` に蓄積され、
ユーザーが手動で反映する。

---

## ディレクトリ一覧

### `actors/`
「行為する主体」を格納する上位カテゴリ。
ここ自体にはファイルを置かず、下位の `persons/` と `collectives/` に分ける。

群像劇では家族や組織も独立した「行為者」として機能するため、
個人と集団を同じ階層の兄弟として扱わず、
`actors` という抽象カテゴリの下に配置する。

#### `actors/persons/`
個人を 1 人 1 ファイルで定義する。
例: `田中誠.md`、`山田花子.md`

#### `actors/collectives/`
集団・組織・家族を 1 つ 1 ファイルで定義する。
例: `田中家.md`、`○○社.md`、`○○サークル.md`

---

### `relations/`
人物間・集団間の関係を格納する。

- `graph.md` — 全関係の一覧。一行一関係で記述し、Director の鳥瞰用。
  「面識なし（重要）」のような**不在の関係**もここに明示する。
- `types.md` — 関係類型の定義。関係の偏り検出の基準となる。
- 個別関係ファイル — 例: `田中誠_and_山田花子.md`
  重要な二者関係の歴史・内的力学・秘密・開示状況を詳述する。

---

### `spaces/`
物語の舞台となる場所を定義する。
単なる地理情報ではなく、**そこで何が可能／不可能か**を含めた
「機能する場」として記述する。

例: `大学構内.md`、`田中家の台所.md`、`駅前の喫茶店.md`

---

### `timeline/`
時系列情報を格納する。

#### `timeline/master.md`
作品全体の年表。すべての主要な出来事を時系列で配置。

#### `timeline/threads/`
個別のプロット糸ごとの時系列。
例: `田中の職歴.md`、`田中家の崩壊史.md`

master が全体地図、threads が個別の糸。
threads を分けるのは、すべての糸を常に読み込まなくて済むようにするため。

---

### `world/`
世界の背景構造。人物・場所よりも抽象度が高い層。

- `structures.md` — 社会構造（職場・家族・コミュニティ・権力構造など）
  Director のネットワーク監査において、**位置の集合**として参照される。
- 必要に応じて: `制度.md`、`経済.md`、`技術水準.md` など作品に応じて追加。

---

### `themes/`
作品の主題・モチーフ。
Director が鳥瞰判断の基準として参照する。

例: `主題_ethics_of_scale.md`、`モチーフ_反復.md`

---

### `TheText/`
確定稿の本文。章ごとにファイル分割する。

例: `chapter_01.md`、`chapter_02.md`

Continuity Checker と Director が継続性の基準として参照する。
ここに置かれたテキストは**確定済み**として扱われ、
執筆中のドラフトは `Output/drafts/` に置くこと。

---

## 作成時のコマンド

ディレクトリを一括作成するには作品フォルダ内で以下を実行する。

```bash
mkdir -p Input/actors/persons
mkdir -p Input/actors/collectives
mkdir -p Input/relations
mkdir -p Input/spaces
mkdir -p Input/timeline/threads
mkdir -p Input/world
mkdir -p Input/themes
mkdir -p Input/TheText
```

Git で空ディレクトリを追跡する場合:

```bash
find Input -type d -empty -exec touch {}/.gitkeep \;
```

---

## 書き込み禁止の原則

Claude Code は `Input/` 配下のすべてのファイルを**読み取り専用**として扱う。
矛盾や修正が必要と判断された場合も、
直接書き換えず `Output/change_proposals.md` に提案として記録する。
この原則は `CLAUDE.md` および `.claude/settings.json` の両方で強制される。
