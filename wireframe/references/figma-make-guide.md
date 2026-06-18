# Figma Make プロンプト生成ガイド

モードBでFigma Make用プロンプトを作るときの詳細仕様。
トーン変換・セクション記述・カラー指定・NGパターンの書き方を定義する。

---

## 基本ルール

| ルール | 理由 |
|--------|------|
| **英語で書く** | Figma Makeの英語理解精度の方が高い |
| **日本語テキストはそのまま** | コピー・見出しは日本語で渡してよい（`「小ロット・短納期」`のまま） |
| **HEXカラーを必ず指定** | 「navy」「dark blue」では生成結果がブレる。`#0B2545`のように書く |
| **px値を明示** | 「large text」ではなく「46px bold」。「generous padding」ではなく「padding 80px top/bottom」 |
| **プレースホルダーの指示を入れる** | 「Gray rectangle (W×Hpx), label: '説明テキスト'」の形式 |
| **NGパターンを末尾に明示** | 書かないと高確率でAIっぽいデザインが出る |

---

## トーン変換表

クライアントの日本語トーン指定を、Figma Makeに渡せる英語設計言語に変換する。

| 日本語トーン | 英語での設計言語 | カラー傾向 | タイポ傾向 |
|------------|----------------|-----------|-----------|
| 信頼感・誠実 | Trustworthy, grounded, evidence-based | Deep navy, charcoal, off-white | Bold sans-serif, generous line-height |
| 先進的・テクノロジー | Forward-looking, precision-engineered, modern | Steel blue accent, near-black, cool white | Geometric sans, tight tracking on headings |
| クリーン・清潔感 | Clean, airy, well-spaced | High contrast, minimal accent, lots of white | Medium weight, ample whitespace |
| 親しみやすい | Approachable, warm, human | Warm gray, soft accent | Rounded sans, relaxed tracking |
| 高級感・プレミアム | Premium, refined, considered | Deep black/dark navy, gold or silver accent | High contrast type scale, restrained use of color |
| 専門性・技術力 | Technical expertise, structural confidence | Monochrome base + single precision accent | Data-like hierarchy, tabular alignment |

**組み合わせ例（今回のテクノプレス工業）：**
「信頼感があり、先進的かつクリーンな印象」
→ `Trustworthy yet forward-looking and clean. Structural confidence, quiet intelligence. Not a dusty factory, not a flashy tech startup.`

---

## Signature element の決め方

Figma Makeプロンプトの「全体方針」に必ず1つ入れる。そのページを他と区別する視覚的な特徴。

| トーン | Signature elementの例 |
|--------|----------------------|
| 先進・技術 | 微細なドットマトリクス or 対角グリッドテクスチャ（4%透明度）|
| クリーン・ミニマル | 極細の水平罫線によるセクション区切り |
| 信頼・誠実 | ロゴ・ISO認証バッジを左罫線付きカードで整列 |
| プレミアム | ヒーローに単色グラデーション（暗→やや明）＋大きな余白 |

---

## セクション記述のフォーマット

```
## SECTION N — セクション名 (背景・サイズの簡潔な説明)

[セクション全体の説明：背景色・縦サイズ・レイアウト方向]

Content description:
- Element 1: [要素の説明。サイズ・色・テキストを具体的に]
- Element 2: ...

[Button / CTA の説明]
```

### 書くべき情報の優先順位

1. **レイアウト構造**（何カラムか・左右どちらか・グリッドか）
2. **背景色と縦サイズ**（`background: #F5F7FA, padding 80px top/bottom`）
3. **各要素のサイズと色**（`26px bold, #1A1A2E`）
4. **テキストコンテンツ**（実際の日本語コピーをそのまま）
5. **プレースホルダー**（`Gray rectangle (360×320px), label: 'ISO認証書の写真（支給）'`）
6. **CTAの色とラベル**（`filled steel blue (#1E6FA6), label: 「お問い合わせ →」`）

---

## カラーパレットのテンプレート

プロンプトの全体方針内に必ず入れる。

```
Color palette:
- Primary: [色名] ([HEX]) — [役割の説明]
- Accent: [色名] ([HEX]) — [使う場面]
- Section alt background: [色名] ([HEX])
- Hero / CTA band: [色名] ([HEX])
- Text headings: [HEX]
- Text body: [HEX]
- Text muted/labels: [HEX]
- Border / divider: [HEX]
```

**クライアントのブランドカラーがある場合**：Primaryとして採用し、Accentはその補色か明度違いで設定する。

---

## 末尾の補足指示（必ず入れる）

```
## 補足指示（Figma Make向け）

- Frame size: 1440px wide. Content max-width 1120px, horizontally centered with auto-layout.
- All sections span full 1440px. Content constrained to 1120px inside.
- Use auto-layout for all sections and card grids.
- Spacing: 8px grid throughout (8/16/24/32/40/48/64/80px).
- Section vertical padding: 80px top/bottom standard (hero: 120〜140px, stats strip: 40px).
- Image placeholders: rectangle filled #D8DDE6, label text centered in #8A8A9A, 13px.
- CTA buttons: [border-radius指定]px radius only. No pill-shaped buttons.
- NEVER use: decorative color bars, accent stripes under titles, gradient blobs, drop shadows on every element, AI-generic patterns.
- Japanese text: use Noto Sans JP or Yu Gothic equivalent.
```

---

## よくあるFigma Make生成ミスと対策

| ミス | 原因 | プロンプトへの追記 |
|------|------|-----------------|
| タイトル下に線が引かれる | 指定なし | `NEVER add underlines or accent lines under headings` |
| 全要素に影がつく | Figmaのデフォルト | `Avoid drop shadows on most elements; use borders instead` |
| クリーム色背景になる | デフォルト | `Use white (#FFFFFF) or specified palette only; avoid warm beige defaults` |
| ボタンがpill形（角丸すぎ）| デフォルト | `CTAs use 2px border-radius only. No pill-shaped buttons.` |
| カラーバー・サイドストライプが入る | AI的な装飾 | `No decorative color bars or accent stripes spanning sections` |
| 日本語が文字化けする | フォント未指定 | `Japanese text: simulate Noto Sans JP bold for headings` |

---

## ファイル出力

```bash
# 保存先
/mnt/user-data/outputs/figma-make-prompt-[ページ名].md

# バージョン管理（トーン変更など）
/mnt/user-data/outputs/figma-make-prompt-[ページ名]-v2.md

# 使い方のメモをチャットに添えて渡す
# 「Figma Makeにセクション2〜3個ずつ分割して投入すると精度が上がります」
```
