# Web_for_Top_change_20260526

Lens Studio アプリ `Tops_change_20260526` の実験補助として、5衣装に対応する
動画を一覧表示するシンプルな静的 Web ページ。

## 構成

```
Web_for_Top_change_20260526/
├── index.html      # メインページ (タイトル: Fashion movies)
├── style.css       # レスポンシブグリッドのスタイル
└── README.md       # 本ファイル
```

ビルド不要。`index.html` をブラウザで開けば動作する。

## Lens Studio アプリとの対応表

Webページの番号は、Lens Studio アプリ
[`Tops_change_20260526`](../LensStudio_project/Tops_change_20260526/) の
ボタン番号と一致するように配置している。

| Webページ番号 | Lens Studio ボタン | 動画ファイル                         |
| :-----------: | :----------------: | ------------------------------------ |
|      01       |         01         | `../data/02.mp4`                     |
|      02       |         02         | `../data/04.mp4`                     |
|      03       |         03         | `../data/black_white_shirt.mp4`      |
|      04       |         04         | `../data/gray_jacket.mp4`            |
|      05       |         05         | `../data/mini.mp4`                   |

## 動画ファイルの参照方法

`fashion/data/` への**相対パス参照** (`../data/<filename>.mp4`)。
データを複製しないため、`fashion/data/` の更新が自動反映される。

## 開き方

### 方法A: ファイルを直接開く
1. Finder で `index.html` をダブルクリック
2. ブラウザ(Safari / Chrome 等)で開く

ブラウザによっては `file://` プロトコルでの動画再生に制限がある場合がある。

### 方法B: ローカルサーバで開く(推奨)
ローカルサーバ経由で開くと安定動作する。
プロジェクトディレクトリで以下を実行:

```sh
# Python が使える環境(macOS 標準)
cd /Users/iniadkambalab/project/fashion/Web_for_Top_change_20260526
python3 -m http.server 8000
```

その後、ブラウザで <http://localhost:8000/> を開く。

ただし `../data/` を参照しているため、サーバの root を一段上げる必要あり:

```sh
cd /Users/iniadkambalab/project/fashion
python3 -m http.server 8000
```

ブラウザで <http://localhost:8000/Web_for_Top_change_20260526/> を開く。

## レイアウト

| 画面幅            | 列数 |
| ----------------- | :--: |
| 1024px 以上       |  3   |
| 768px〜1023px     |  2   |
| 767px 以下        |  1   |

各動画は `<video controls muted loop playsinline>` 属性で表示。
被験者は再生ボタンをクリックして動画を見る方式。
