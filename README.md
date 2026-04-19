# KITAcore — Public Tools & Guides

note記事の補足ページ・取説・インタラクティブガイドを公開しているリポジトリ。

🔗 **公開URL:** `https://Goo-dev0505.github.io/kitacore.dev/`  
📝 **note:** `https://note.com/ktcrs1107`

---

## 現在の公開ページ

| # | カテゴリ | ページ名 | ファイル | 状態 |
|---|---|---|---|---|
| 01 | 取説 | NAME Generator 取扱説明書 | `name-generator-manual.html` | ✅ LIVE |
| 02 | 記事補足 | SKI RANKING 2 遊び方ガイド | `ski-r2-guide.html` | ✅ LIVE |
| 03 | 記事補足 | AIの7つの力 完全ガイド | `ai-7powers.html` | ✅ LIVE |

---

## ファイル構成

```
kitacore.dev/
├── index.html                 ← ポータルTOP（カード一覧）
├── name-generator-manual.html
├── ski-r2-guide.html
├── ai-7powers.html
└── README.md                  ← このファイル
```

---

## ページを追加するとき（6ステップ）

### STEP 1 — HTMLファイルを用意する

ファイル名のルール：
```
✅ ski-r2-guide.html        読みやすい・短い・バージョン込み
✅ ai-7powers.html          内容が一目でわかる
❌ new_page_final_v3.html   長い・わかりにくい
❌ index2.html              意味がない
```

---

### STEP 2 — index.html にカードを追加する

カテゴリは2種類。追加先を選ぶ。

**取説カード（黒背景セクション）**

```html
<!-- ══ 使い方を読む (DARK) ══ の <div class="cards"> 内に追加 -->
<a class="card-d rv2" href="新ファイル名.html">
  <div class="ct">
    <span class="card-num">02</span>  <!-- 番号を+1 -->
    <div>
      <div class="card-status">FIELD MANUAL<br>VERSION 1</div>
      <span class="live-badge">● LIVE</span>
    </div>
  </div>
  <div class="cb">
    <span class="card-tag">MANUAL · カテゴリ名</span>
    <h3 class="card-title">タイトル<br>サブタイトル</h3>
    <p class="card-hook">読者の疑問・課題を1〜2行で。</p>
    <span class="card-get">読むと、○○ができる</span>
  </div>
  <div class="cf">
    <span class="card-date">2026.xx · タグ</span>
    <span class="card-arr">→</span>
  </div>
</a>
```

**記事補足カード（オレンジ背景セクション）**

クラスを `card-d` → `card-o`、`card-date` → `card-date-o` に変えるだけ：

```html
<!-- ══ 記事と一緒に読む (ORANGE) ══ の <div class="cards"> 内に追加 -->
<a class="card-o rv2" href="新ファイル名.html">
  <div class="ct">
    <span class="card-num">03</span>  <!-- 番号を+1 -->
    <div>
      <div class="card-status">GUIDE<br>2026</div>
      <span class="live-badge">● LIVE</span>
    </div>
  </div>
  <div class="cb">
    <span class="card-tag">GUIDE · カテゴリ名</span>
    <h3 class="card-title">タイトル<br>サブタイトル</h3>
    <p class="card-hook">読者の疑問・課題を1〜2行で。</p>
    <span class="card-get">読むと、○○ができる</span>
  </div>
  <div class="cf">
    <span class="card-date-o">2026.xx · タグ</span>  <!-- card-date-o -->
    <span class="card-arr">→</span>
  </div>
</a>
```

---

### STEP 3 — ブートシーケンスを更新する

JS内の `lines` 配列にページを追加。`d:` の値は前の行 +180 くらいが目安。

```js
const lines = [
  { t:'KITACORE PORTAL v2026 INITIALIZING...', c:'hi', d:0 },
  { t:'LOADING: PUBLIC TOOLS & GUIDES',        c:'',   d:260 },
  { t:'  [取説]      NAME GENERATOR MANUAL  ■', c:'or', d:500 },
  { t:'  [補足 01]   SKI RANKING 2 GUIDE    ■', c:'or', d:680 },
  { t:'  [補足 02]   AI 7 POWERS GUIDE      ■', c:'or', d:860 },
  { t:'  [補足 03]   新ページ名             ■', c:'or', d:1040 },  // ← 追加
  { t:'ALL SYSTEMS OPERATIONAL',               c:'hi', d:1240 },
  { t:'LAUNCHING...',                          c:'hi cur', d:1380 },
];
```

---

### STEP 4 — ティッカーを更新する

`.t-track` 内のテキストを追加。**ループのため2か所同じものを書く。**

```html
<div class="t-track">
  <!-- 既存のti要素 -->
  <span class="ti">新ページ名 — <span class="ot">LIVE</span></span>  ← 追加
  <!-- ...1セット目の末尾 -->

  <!-- 既存のti要素（コピー） -->
  <span class="ti">新ページ名 — <span class="ot">LIVE</span></span>  ← 追加
  <!-- ...2セット目の末尾 -->
</div>
```

---

### STEP 5 — カウンターを更新する

ページ数の数字を変える：

```js
window.addEventListener('load', () => {
  countUp('cnt-p', 4, 600);  // ← ページ数を+1
  countUp('cnt-c', 2, 700);  // カテゴリ数（変わらなければそのまま）
});
```

---

### STEP 6 — GitHubにアップロード

```
変更ファイル:
  - index.html（更新済み）
  - 新ファイル名.html（新規）

GitHub操作:
  Add file → Upload files → ドラッグ → Commit changes
```

---

## 更新ログ

```
2026.04  初回公開
         - name-generator-manual.html（取説）
         - ski-r2-guide.html（記事補足）
         - ai-7powers.html（記事補足）
```

> 新ページを追加したらここに1行追記する。

---

## Author

**にーさん / KITAcore**
- note: https://note.com/ktcrs1107
- GitHub: https://github.com/Goo-dev0505
