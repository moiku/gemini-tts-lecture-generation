Marp研究スライド作成ガイド（academic-tmlテーマ使用）
基本設定
yaml---
marp: true
theme: academic-tml
paginate: true
math: katex
---
スライド構造の基本ルール
1. ページ区切りとヘッダー

スライドの区切り：---（3つのハイフン）
各スライドの見出し：<!-- _header: セクション名 -->
重要：ヘッダーがスライドの主見出しとなるため、本文中では#（h1）を使わず、##（h2）から開始する

2. タイトルスライド（leadクラス）
markdown<!-- _class: lead -->

# 研究タイトル

### サブタイトル（任意）

発表者名
所属・日付
3. 通常スライド
markdown<!-- _header: セクション名 -->

## 見出し（h2から開始）

本文テキスト

### 小見出し（h3）

- 箇条書き項目
  - サブ項目（自動的に0.9倍サイズ）
デザイン要素の使い方
1. テキスト装飾

太字：**テキスト**
<span class="marker">マーカー強調</span>：<span class="marker">重要箇所</span>

<div class="bubble">吹き出し強調</div>：
```html
<div class="bubble">
強調したい内容
</div>
```

2. 2段組
```html
<div class="two-columns">
 <div class="column">
左側
 </div>
 <div class="column">
右側
 </div>
</div>
```

3. 数式

インライン数式：$E = mc^2$
ブロック数式：
markdown$$
\frac{\partial u}{\partial t} = \alpha \nabla^2 u
$$

4. 画像

中央配置：![w:600 center](画像パス)
幅指定：![w:800](画像パス)
高さ指定：![h:400](画像パス)

5. コードブロック
markdown```python
def hello():
    print("Hello, World!")

### 5. 引用・参考文献
ページ下部に配置される脚注として使用：
```markdown
> 参考文献：著者名（年）『タイトル』出版社
カラーパレット
CSSで定義された以下の色を活用：

背景色：#F6F9F6（薄緑）
メインカラー：#0A2D92（濃紺）
アクセント1：#A5B8E8（薄青）
アクセント2：#FFADB1（薄ピンク）
強調色：#E60012（赤）
テキスト：#3E3A39（濃灰）

スライド作成のベストプラクティス
1. コンテンツ構成

1スライド1メッセージ
箇条書きは最大5-7項目
図表を積極的に活用
適度な余白を確保
内容に応じて2段組を適切に使用

2. 視覚的な工夫

重要キーワードは<span class="marker">でハイライト
結論や重要な発見は<div class="bubble">で強調
絵文字の活用（📊 📈 ✅ ⚠️ 💡 🔍 など）
矢印での流れ表現（→ ← ↔ ⇒）

3. プレゼンテーション全体の流れ

タイトルスライド（leadクラス）
概要・アウトライン
背景・動機
方法・アプローチ
結果・成果
考察・議論
結論・今後の展望
謝辞・参考文献

実装例
markdown---
marp: true
theme: academic-tml
paginate: true
math: katex
---

<!-- _class: lead -->

# 深層学習を用いた画像認識の高精度化

### ～転移学習による少量データでの実現～

山田太郎
〇〇大学大学院 情報工学専攻
2025年6月6日

---

<!-- _header: 研究背景 -->

## なぜこの研究が必要か？

- 従来の手法の課題
  - 大量の学習データが必要 💰
  - 計算コストが高い ⏱️
  - 専門知識が必要 🎓

<div class="bubble">
少量データでも高精度な認識を実現したい！
</div>

---

<!-- _header: 提案手法 -->

## 転移学習アプローチ

![w:600 center](diagram.png)

<span class="marker">事前学習済みモデル</span>を活用することで：

- ✅ 学習時間を大幅短縮
- ✅ 少量データでも高精度
- ✅ 実装が容易

> 参考：He et al. (2016) "Deep Residual Learning for Image Recognition"
注意事項

ヘッダーセクション名は本文の一部として扱う
h1（#）はleadページのタイトルのみで使用
通常ページではh2（##）から開始
CSSクラス（marker、bubble）を効果的に活用
図表には必ず適切なサイズ指定を行う
