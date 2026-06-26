# Web_for_Top_change_20260526 (公開URL: fashion-experiment-v1)

Lens Studio アプリ `Tops_change_20260526` の実験補助として、5衣装に対応する
動画と静止画を一覧表示するシンプルな静的 Web ページ。

**公開実験用 GitHub Pages**:
<https://iniadkambalab.github.io/fashion-experiment-v1/>

> GitHub 上のリポジトリ名は `fashion-experiment-v1`。
> ローカルのディレクトリ名は `Web_for_Top_change_20260526` のまま運用している。

## 構成

```
Web_for_Top_change_20260526/
├── index.html          # メインページ (タイトル: Fashion movies)
├── style.css           # レスポンシブグリッドのスタイル
├── .nojekyll           # GitHub Pages の Jekyll 処理を無効化
├── data/               # ページが参照する動画・画像 (リポジトリ内に同梱)
│   ├── *.mp4           # 動画5本 + snapcode.png
│   └── static_image/   # 衣装の静止画5枚
└── README.md           # 本ファイル
```

ビルド不要。`index.html` をブラウザで開けば動作する。

## 表示仕様 (デフォルト非表示トグル)

Movies / Clothes の各セクションは **初期状態では中身を非表示**にしている。
タイトル横のボタン（初期表示 `OFF`）を押すと表示が切り替わる:

- `OFF` (初期) → 中身は非表示
- ボタンをクリック → `ON` になり中身を表示
- 再度クリック → `OFF` に戻り非表示 (トグル方式)

## Lens Studio アプリとの対応表

Webページの番号は、Lens Studio アプリ
[`Tops_change_20260526`](../LensStudio_project/Tops_change_20260526/) の
ボタン番号と一致するように配置している。

| Webページ番号 | Lens Studio ボタン | 動画ファイル                    | 静止画ファイル                              |
| :-----------: | :----------------: | ------------------------------- | ------------------------------------------- |
|      01       |         01         | `data/02.mp4`                   | `data/static_image/02_top_static.png`       |
|      02       |         02         | `data/04.mp4`                   | `data/static_image/04_top_static.png`       |
|      03       |         03         | `data/black_white_shirt.mp4`    | `data/static_image/white_shirt_static.png`  |
|      04       |         04         | `data/gray_jacket.mp4`          | `data/static_image/gray_jacket_static.png`  |
|      05       |         05         | `data/jeans.mp4`               | `data/static_image/jeans_static.png`|

## 動画・画像ファイルの参照方法

GitHub Pages 公開のため、参照ファイルを `data/` 配下に**リポジトリ内へ同梱**している
（元データは `fashion/data/` からコピー）。`index.html` からは `data/<filename>` の
**相対参照**で読み込む。元データを更新した場合は `data/` 配下へ再コピーが必要。

## 開き方 (ローカル確認)

### 方法A: ファイルを直接開く
1. Finder で `index.html` をダブルクリック
2. ブラウザ(Safari / Chrome 等)で開く

ブラウザによっては `file://` プロトコルでの動画再生に制限がある場合がある。

### 方法B: ローカルサーバで開く(推奨)
データを同梱したため、このディレクトリ直下をルートにすればよい:

```sh
cd /Users/iniadkambalab/project/fashion/Web_for_Top_change_20260526
python3 -m http.server 8000
```

ブラウザで <http://localhost:8000/> を開く。

## レイアウト

| 画面幅            | 列数 |
| ----------------- | :--: |
| 1024px 以上       |  5   |
| 768px〜1023px     |  3   |
| 767px 以下        |  1   |

各動画は `<video controls muted loop playsinline>` 属性で表示。
被験者はボタンでセクションをONにし、再生ボタンをクリックして動画を見る方式。
