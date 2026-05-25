# MAISON D'OMBRE — beauty-salon/noir Spec

**Status:** Approved
**Author:** torifo
**Created:** 2026-05-25
**Updated:** 2026-05-25

---

## 1. Overview

### Problem Statement
高所得層の女性は、日中の白く明るいサロンとは別軸として「夜に静かに整えにいく場所」を求めている。しかし国内の高級美容サロンの Web 表現は、白基調の自然光・笑顔・ビフォーアフター訴求にほぼ統一されており、「夜の儀式としての美」を扱う設計言語が空席になっている。暗背景に切り替えると、途端にナイトクラブ／ホストクラブ風の俗な装飾に転落してしまうため、「夜の格」を Web 上で成立させるのが極めて難しい。

### Goal
架空ブランド **MAISON D'OMBRE**（メゾン・ドンブル、影の館）を、ヘア × スパを統合した夜のメゾンとして実装する。Aman Spa の暗背景 × serif × 余白の品格を骨格にしつつ、Le Labo 的アポセカリ（薬種商）の道具感と、フランス語の小さな囁きで「下品にならない夜の美の儀式」を成立させる。利用者が「23時、ここに行けば自分が静かに整えられる」と感じる温度を、装飾ではなくタイポグラフィ・余白・蝋燭の灯だけで作る。

### Non-Goals
- 価格・割引キャンペーン・期間限定の前面化（高級メゾンの品位を損なう）
- ビフォーアフター訴求、施術前後の比較写真
- スタッフ全員集合の笑顔写真、顔の正面アップ
- 「予約はこちら」「今すぐ」のような直接的・煽り CTA
- カート／決済／オンライン入会フォーム（来店予約・お問合せのみ）
- 多色配色・グラデーション・ガラス効果・装飾的アイコン
- ナイトクラブ／バー的な装飾（ネオン、グリッター、装飾文字）

---

## 2. User Stories

| ID | Persona | Want to | So that |
|----|---------|---------|---------|
| US-01 | 34歳・外資コンサル女性・既婚 | 夜遅くに静かに整えられる場所を知りたい | 平日の終わりに自分を取り戻せる |
| US-02 | 38歳・経営者女性・独身 | ヘアとスパを同じ夜に同じ場所で受けたい | 移動時間と気持ちの切替コストを払いたくない |
| US-03 | 41歳・ブランド勤務女性 | サロンの「格」と「静けさ」を事前に確認したい | 場違いにならないか、騒がしくないか判断してから問合せできる |
| US-04 | 36歳・舞台関係者 | 顔写真や派手な広告ではなく、メゾンの哲学で選びたい | 信頼に値する場所だと自分で納得して通いたい |

---

## 3. Functional Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-01 | 暗背景（near-black `#0e0a08`） × 真鍮 `#b8a47a` × アイボリー `#ebe6da` の 3 色基調。それ以外の色は使わない | P0 |
| FR-02 | ヒーローに「蝋燭の灯」または「ガラス器」または「首筋のシルエット」のいずれかの暗い写真 1 枚と、serif の短いフランス語＋日本語コピー | P0 |
| FR-03 | LE RITUEL（儀式）セクション：来館から退館までの夜の流れを 4〜5 ステップで提示（受付・浄め・施術・休息・送り出し） | P0 |
| FR-04 | LES SOINS（施術一覧）：ヘア／スパ／頭浸浴／フェイシャル等を最大 6 項目。各項目はフランス語名＋日本語小見出し＋短い説明 | P0 |
| FR-05 | LES ARTISANS（職人紹介）：顔写真は使わず、手・道具・後ろ姿のマクロ写真と、肩書き・修業歴の抽象タグのみで構成 | P0 |
| FR-06 | LA MAISON（メゾン紹介）：内装の暗い写真と、建築・素材（黒大理石・革・真鍮）の言及 | P0 |
| FR-07 | LES HEURES（営業時間）：14:00–24:00（最終受付 22:00）であることを強調し、「夜のメゾン」であることを構造的に明示 | P0 |
| FR-08 | RÉSERVATION：「ご予約」「お問合せ」の丁寧な招きの言葉のみ。電話番号・予約フォームへの導線は静かに 1 か所のみ | P0 |
| FR-09 | ナビは固定上部、リンクホバー時のみ真鍮色の細い下線（1px）が左から伸びる | P1 |
| FR-10 | スクロール時のフェードイン（IntersectionObserver、0.8 秒）。視差スクロール禁止、`prefers-reduced-motion` 完全対応 | P0 |
| FR-11 | 840px 以下で 1 カラム化、LE RITUEL は時刻軸の縦リストに変形 | P0 |
| FR-12 | フッターに小さく "Par la nuit, la beauté."（夜によって、美は）の一文 | P1 |

---

## 4. Key Design Decisions

| Decision | Chosen | Rationale | Rejected |
|----------|--------|-----------|----------|
| 基調色 | near-black `#0e0a08` + 真鍮 `#b8a47a` + アイボリー `#ebe6da` | 温度のある黒（赤茶寄り）で、メゾンの革・木・蝋燭の暖かさを示唆。純黒 `#000` は冷たく重い | 純黒 #000、ネイビー、ダークブラウン |
| アクセント | くすんだ真鍮 1 色のみ | ピカピカの金は成金的になる。経年したアンティーク真鍮で「静かな格」と「夜の灯」を両立 | 純金、ローズゴールド、銀 |
| 補助色 | ash `#3a3a3a` を区切り線・キャプションに限定使用 | 暗背景上のヒエラルキー分離のため。本文には使わない | 暗背景上にグレー文字を多用 |
| 見出し書体 | Didot or Playfair Display（serif） | 高コントラストのモダン・セリフ。Vogue 等のメゾン媒体由来の格。ディスプレイサイズで細い縦線が映える | Cormorant（甘い）、Bodoni（硬すぎ）、Sans 全般 |
| 和文見出し | Noto Serif JP（Weight 500 以上） | 明朝の格と暗背景上での視認性を両立。500 未満だと暗背景で痩せる | Yu Mincho（Web 配信に不安）、ゴシック系全般 |
| 本文書体 | Inter（補助） | フランス語・英語・数字のメタ情報・営業時間など事実情報の可読性のため。見出しには絶対使わない | 本文も serif で統一（情報の手触りが平坦になる） |
| 装飾 | 真鍮の hairline（1px）と過剰な余白のみ | Aman の "Less but precious"。装飾の多さではなく余白・素材・タイポグラフィで格を作る | 罫線多用、グラデーション、ガラス効果、装飾アイコン |
| コピー言語 | フランス語見出し＋日本語小見出し＋日本語本文の三層 | フランスのメゾン由来の格と、日本人ユーザーの理解可能性を両立。英語より声が低く落ち着く | 英語のみ、フランス語のみ、日本語のみ |
| 写真 | 顔を映さない（首筋・後ろ姿・手・道具・蝋燭・ガラス器・髪のシルエット） | ビフォーアフター訴求・笑顔訴求を構造的に拒否。「夜の儀式」の想像の余地で品位を保つ | 顔のアップ、施術中の笑顔、ビフォーアフター |
| 写真トーン | 暗背景、ランプ／蝋燭の人工光、低彩度、縦長 portrait | 自然光は「白い昼の美」になる。夜のメゾンは人工光でしか成立しない | 自然光・明るい背景・正方形クロップ |
| CTA トーン | 「ご予約」「お問合せ」「Réservation」のみ | 直接的な行動命令は俗。丁寧な招きの言葉で「来てもよろしいですか」のニュアンスを作る | 「予約する」「今すぐ」「無料相談」 |
| Hover 演出 | 真鍮の hairline が左から右へ伸びる + 文字色がアイボリーへ | 「灯が一筋ともる」感覚。装飾的拡大・影は禁 | スケール変化、ドロップシャドウ、色のフラッシュ |
| 営業時間 | 14:00–24:00（最終受付 22:00） | 「夜のメゾン」を文字情報として構造的に証明する。朝開店だと矛盾する | 10:00–20:00 等の一般的時間帯 |
| 職人紹介 | 顔写真なし、手・道具のマクロのみ | 個人崇拝でなくメゾン全体の格を売る思想。顔出しはサロン全般の様式に流される | 顔写真＋プロフィール＋SNS リンク |

---

## 5. Design System

```css
/* Palette */
--bg:        #0e0a08;   /* near-black, 温度のある黒。革・蝋燭の影 */
--bg-soft:   #181210;   /* セクション分割・カード背景 */
--ink:       #ebe6da;   /* アイボリー, 本文 */
--ink-mute:  #8a8276;   /* 補足・キャプション・メタ情報 */
--brass:     #b8a47a;   /* 唯一の差し色（アンティーク真鍮） */
--brass-soft:#6a5e44;   /* hairline / 区切り線 */
--ash:       #3a3a3a;   /* 暗背景上の薄い区切り線 */

/* Typography */
--font-display: 'Playfair Display', 'Didot', 'Noto Serif JP', serif;
--font-serif-jp:'Noto Serif JP', serif;            /* 和文見出し（Weight 500+） */
--font-body:    'Inter', 'Noto Serif JP', sans-serif;
--font-meta:    'Inter', sans-serif;               /* 時刻・番号・住所等の事実情報 */

/* Scale */
--fs-hero:    clamp(56px, 9vw, 144px);   /* serif display, 細め */
--fs-h2:      clamp(32px, 4vw, 64px);
--fs-h3:      clamp(20px, 2.4vw, 32px);
--fs-body:    16px;
--fs-cap:     12px;
--lh-body:    1.9;                       /* 行間広め */
--lh-display: 1.15;
--tracking-display: 0.04em;
--tracking-eyebrow: 0.32em;              /* "LE RITUEL" 等の小見出し */
--tracking-body:    0.02em;

/* Layout */
--max:        1280px;
--pad-x:      clamp(24px, 5vw, 80px);
--gap-section:clamp(96px, 14vh, 192px);  /* セクション間の過剰な余白 */
--gap-block:  clamp(48px, 8vh, 96px);

/* Motion */
--ease:       cubic-bezier(.2,.7,.2,1);
--dur:        .8s;                       /* ゆっくり系 */
--dur-hover:  .4s;

/* Borders */
--hairline:   1px solid var(--brass-soft);
--hairline-strong: 1px solid var(--brass);
```

### セクション構成

```text
index.html
├── header.nav              固定・透明→スクロール時に near-black へ
├── section.hero            蝋燭／ガラス器の暗写真 + "Par la nuit." 短いコピー
├── section.maison          LA MAISON — メゾンの哲学と建築素材
├── section.rituel          LE RITUEL — 来館から退館までの 4〜5 ステップ
├── section.soins           LES SOINS — ヘア／スパ／頭浸浴等の施術一覧
├── section.artisans        LES ARTISANS — 職人紹介（顔なし・手と道具）
├── section.heures          LES HEURES — 営業時間 14:00–24:00 と住所
└── footer                  "Par la nuit, la beauté."
```

### コピーサンプル

```text
[Hero]
Par la nuit.
夜のために、整える。
                                        — Maison d'Ombre

[Section eyebrow]
— LE RITUEL —     一夜の流れ

[CTA]
Réservation         ご予約
Contact             お問合せ

[Footer]
Par la nuit, la beauté.
夜によって、美は。
```

---

## 6. References

### 参照サイト
- [Aman Spa](https://www.aman.com/spa) — 暗背景 × serif × 過剰な余白の品格、CTA は "Discover" / "Explore" の招きの言葉。「装飾の少なさで luxury を成立させる」設計思想
- [uka](https://uka.co.jp/) — 番号付きセクション（01/03 等）の品位、詩的な日本語コピーのトーン（「うれしくって、うつくしいほうへ」のような lyrical な声）
- [PEEK-A-BOO](https://www.peek-a-boo.co.jp/) — 1977 年創業の heritage 訴求、職人哲学（「日々葛藤し精進しながら」）を前面に出す restraint の設計
- [Le Labo](https://www.lelabo.com/) — アポセカリ（薬種商）の道具感、フランス語＋英語の囁き、minimalist craft のトーン
- [Sisley Paris](https://www.sisley-paris.com/) — French house の格と落ち着いた声色

### Google Fonts
- [Playfair Display](https://fonts.google.com/specimen/Playfair+Display) — display serif（高コントラスト、メゾン媒体由来）
- [Noto Serif JP](https://fonts.google.com/noto/specimen/Noto+Serif+JP) — 和文明朝（Weight 500 以上を使用）
- [Inter](https://fonts.google.com/specimen/Inter) — 補助 sans（メタ情報・営業時間・住所のみ）

### 内部参照
- [PLAN_BEAUTY_SALON.md](../../PLAN_BEAUTY_SALON.md) — シリーズ上位計画（高級感の出し方 10 項目、写真戦略、動き方針）
- [stationery/mono/spec.md](../../stationery/mono/spec.md) — spec フォーマットの基準
- [fitness-gym/salon/spec.md](../../fitness-gym/salon/spec.md) — 暗色系トーン × serif の参考（ホテルラウンジ軸の高級感）
