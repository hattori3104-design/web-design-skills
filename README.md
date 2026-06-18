# web-design-skills

Claude（Cowork）で使えるウェブ制作スキル集。
フリーランスデザイナー・小規模制作会社向けに、ヒアリングから提案書・ワイヤーフレームまでの実務フローをスキル化しています。

---

## 収録スキル（3本）

| スキル | 役割 | 主な出力物 |
|--------|------|-----------|
| [`web-strategy`](./web-strategy/) | Web戦略の立案・サイトマップ設計 | 戦略設計書・サイトマップ・ファネル設計 |
| [`web-proposal`](./web-proposal/) | 提案書の組み立て・ファイル生成 | .docx / .pptx / .md |
| [`wireframe`](./wireframe/) | ワイヤーフレーム・Figma Makeプロンプト生成 | HTMLワイヤー / Figma Makeプロンプト |

### スキルチェーンのフロー

```
ヒアリング
  ↓
web-strategy ── 戦略・ファネル・サイトマップを設計
  ↓
wireframe    ── HTMLワイヤーフレーム → Figma Makeプロンプト
  ↓
web-proposal ── キックオフ設計提案書（.docx）または受注前提案（.pptx）
```

---

## インストール方法

### 方法A：.skill ファイルでインストール（推奨）

1. [Releases](../../releases) から最新の `.skill` ファイルをダウンロード
2. Cowork の設定画面からインストール

### 方法B：手動でコピー

1. このリポジトリをクローン or ダウンロード
2. スキルフォルダを Cowork のスキルディレクトリ（通常 `/mnt/skills/user/`）にコピー

```bash
git clone https://github.com/YOUR_USERNAME/web-design-skills.git
cp -r web-design-skills/web-strategy  /path/to/skills/user/
cp -r web-design-skills/web-proposal  /path/to/skills/user/
cp -r web-design-skills/wireframe     /path/to/skills/user/
```

---

## 各スキルの詳細

### web-strategy

Web制作のための調査・企画・提案スキル。ヒアリング情報をもとに、競合調査・ターゲット設計・ファネル設計・サイトマップまでを生成します。

**トリガー例：**
- 「Webサイトを作りたい」「リニューアルしたい」
- 「競合サイトを調べたい」「サイトマップを考えたい」
- 「BtoBサイトの戦略を考えたい」「CVRを改善したい」

**内蔵リファレンス：**
- `references/btob-web-strategy.md` — BtoB特有のKPI設計・3層ペルソナ・ファネル設計
- `references/conversion-optimization.md` — CVR改善・行動科学・速度・計測
- `references/copywriting.md` — キャッチコピー・ボディコピー・CTA設計

---

### web-proposal

web-strategyの成果物を、クライアントの合意を取る提案書に組み立てるスキル。2タイプに対応します。

| タイプ | 目的 | 出力形式 |
|--------|------|---------|
| 受注前提案 | 「この方向でやりましょう」と口説く | .pptx |
| キックオフ設計提案 | 「この設計・進行で進めます」と合意を取る | .docx |

どちらも .md を常に併産します。

**カスタマイズが必要な箇所：**
`references/proposal-patterns.md` 内の「制作側（あなたのスタジオ名）」を自分の屋号・会社名に変更してください。

---

### wireframe

HTMLワイヤーフレームとFigma Make用プロンプトを生成する2モードのスキル。

| モード | 出力 | 用途 |
|--------|------|------|
| A: HTMLワイヤー | グレースケール・アノテーション付きHTMLファイル | ブラウザ確認・クライアント共有 |
| B: Figma Makeプロンプト | テキストプロンプト（.md） | Figma Make（AI生成機能）への入力 |

**内蔵リファレンス：**
- `references/html-wireframe-guide.md` — CSSトークン・コンポーネント・アノテーション仕様
- `references/figma-make-guide.md` — トーン変換表・セクション記述・NGパターン対策

---

## 動作環境

- Claude（Anthropic）の Cowork 環境
- docx生成には `npm install docx` が必要（web-proposalのキックオフ提案書を使う場合）
- pptx生成には pptx スキル（`/mnt/skills/public/pptx/`）が必要

---

## カスタマイズ

各スキルは以下の点を自分の業務に合わせて変更することを推奨します。

| スキル | カスタマイズ推奨箇所 |
|--------|-------------------|
| web-strategy | `references/` 内の業種・規模の前提（現状はBtoB・中小企業向けに最適化） |
| web-proposal | `references/proposal-patterns.md` の「制作側（あなたのスタジオ名）」 |
| wireframe | `references/figma-make-guide.md` のトーン変換表（自社の得意トーンを追加） |

---

## ライセンス

MIT License — 商用利用・改変・再配布可。

---

## 作者

[Sakumadesign](https://sakumadesign.com)
フリーランスデザイナー。BtoB企業のWeb戦略・制作・ブランディングを担当。

フィードバック・PRは歓迎します。
