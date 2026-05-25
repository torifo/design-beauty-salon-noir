# MAISON D&rsquo;OMBRE — beauty-salon/noir

design シリーズ第 8 弾「高級感漂う美容サロン」の `noir` ペルソナ実装。
架空の高級美容メゾン **MAISON D&rsquo;OMBRE**（メゾン・ドンブル、影の館）— ヘアとスパを統合した「夜のメゾン」。

- **Domain**: `design.beauty-salon-noir.riumu.net`
- **Theme**: 温度のある黒 × アンティーク真鍮 × アイボリーで、夜だけ灯る美の儀式
- **Status**: 架空ブランド — デザイン研究作品（実在しません）

## ペルソナの輪郭

- 高所得層の女性、夜に静かに整えにいく場所を探す層
- 日中の白いサロンとは別軸として「夜の儀式としての美」を扱う
- 顔写真を排し、蝋燭・ガラス器・首筋・手・道具で品位を保つ
- 営業時間 14:00–24:00（最終受付 22:00）を構造的に明示

## 設計の核

| 軸 | 採用 |
|---|---|
| 配色 | near-black `#0e0a08` + 真鍮 `#b8a47a` + アイボリー `#ebe6da` |
| 書体 | Playfair Display + Noto Serif JP (500+) + Inter (補助) |
| コピー | フランス語見出し + 日本語小見出し + 日本語本文の三層 |
| Hover | 真鍮 hairline が左から右へ伸びる + 文字色変化のみ |
| Motion | 0.8 秒のフェードイン、`prefers-reduced-motion` 完全対応 |
| 写真 | 顔を映さない — 蝋燭・ガラス器・首筋・手・道具のマクロ |

## セクション構成

- **Hero** — *Par la nuit.* 夜のために、整える。蝋燭の灯
- **La Maison** — メゾンの哲学と建築素材（黒大理石・革・真鍮）
- **Le Rituel** — 来館 20:00 から退館 23:00 までの 5 ステップ
- **Les Soins** — ヘア／スパ／頭浸浴／フェイシャル等 6 項目
- **Les Artisans** — 顔を映さない職人紹介（手と道具のみ）
- **Les Heures** — 14:00–24:00 を視覚的に強調
- **Footer** — *Par la nuit, la beauté.*

## ファイル

```
noir/
├── index.html           — シングルファイル実装
├── spec.md              — 仕様書
├── README.md            — 本書
├── DESIGN_LEARNINGS.md  — 実装知見
├── .nojekyll            — GitHub Pages 用
└── CNAME                — design.beauty-salon-noir.riumu.net
```

## 同シリーズ

- [`ivoire`](../ivoire/) — 銀座白基調メゾン
- [`rouge`](../rouge/) — フレンチ・ベルベット
- [`wabi`](../wabi/) — 和モダン・侘び寂び
