# 中央文字画像生成ツール

テキストを完璧に中央配置したSVG画像を生成するWebツールです。Canvas APIのmeasureText()とactualBoundingBoxを使用して、数学的に正確な中央配置を実現します。

## 概要

このツールは、日本語を含む多言語のテキストを画像の中央に完璧に配置したSVG画像を生成できるWebアプリケーションです。NFT画像作成やデザイン作業などに活用できます。

## 主な機能

- **精密な文字中央配置**: Canvas APIを使用した数学的に正確な中央配置
- **多言語対応**: 日本語、中国語、韓国語、英語など多様な文字セットに対応
- **リアルタイムプレビュー**: パラメータ変更を即座に反映
- **2つの表示モード**:
  - **完璧配置**: 実際の出力画像
  - **デバッグビュー**: 中心線やバウンディングボックスを表示する検証用表示
- **SVGダウンロード**: 両方の表示モードをSVGファイルとして保存可能
- **作者名表示**: 画像右下に作者名を小さく表示する機能
- **詳細なメトリクス表示**: テキストの寸法情報をリアルタイム表示

## 使用方法

### アクセス

GitHub Pagesで公開されています：
[https://genhirano.github.io/UnownedMintImageCreator/text-centering-tool.html](https://genhirano.github.io/UnownedMintImageCreator/text-centering-tool.html)

### 操作手順

1. **表示テキスト**に配置したい文字を入力
2. **フォントサイズ**と**フォントファミリー**を調整
3. **キャンバスサイズ**で出力画像サイズを設定（100-600px）
4. 必要に応じて**作者名**を入力
5. プレビューを確認し、「完璧配置をSVGでダウンロード」ボタンでダウンロード

### 対応フォント

- **英語・西欧言語**: Arial, Times New Roman, Georgia, Courier New, Impact, Comic Sans MS
- **日本語**: Meiryo（ひらがな・カタカナ・漢字）
- **中国語**: Microsoft YaHei（簡体字）, Microsoft JhengHei（繁体字）
- **韓国語**: Malgun Gothic（ハングル）

## 技術仕様

### アーキテクチャ
- **フロントエンド**: 純粋なHTML + CSS + JavaScript（単一ファイル）
- **描画エンジン**: HTML5 Canvas API + SVG生成
- **ホスティング**: GitHub Pages

### 画像仕様
- **形式**: SVG（ベクター形式）
- **アスペクト比**: 正方形（1:1）
- **サイズ**: カスタマイズ可能（100-600px）
- **背景色**: 白（#FFFFFF）
- **メインテキスト色**: ダークグレー（#333333）
- **作者名色**: ミディアムグレー（#666666）

### 中央配置アルゴリズム

1. Canvas APIの`measureText()`で基本的なテキスト寸法を取得
2. `actualBoundingBox`プロパティで実際の文字境界を計算
3. ピクセル単位での精密な境界検出を実行
4. 両方の結果を比較し、より適切な値を選択
5. 数学的な中央座標を算出してテキストを配置

## 開発・カスタマイズ

### ローカル実行

```bash
# リポジトリをクローン
git clone https://github.com/genhirano/UnownedMintImageCreator.git
cd UnownedMintImageCreator

# シンプルなWebサーバーで実行
python3 -m http.server 8080
# または
npx serve .

# ブラウザで http://localhost:8080/text-centering-tool.html にアクセス
```

### ファイル構成

```
UnownedMintImageCreator/
├── text-centering-tool.html  # メインアプリケーション（単一ファイル）
├── README.md                 # このファイル
└── .github/workflows/        # GitHub Pages自動デプロイ設定
    └── deploy.yml
```

### カスタマイズポイント

- **デフォルト値**: HTML内のJavaScriptで変更可能
- **スタイル**: `<style>`セクションのCSSを編集
- **対応フォント**: フォント選択の`<option>`要素を追加/削除
- **カラーパレット**: CSS変数やJavaScript内の色設定を変更

## デプロイ

mainブランチへのプッシュ時にGitHub Actionsが自動的にGitHub Pagesにデプロイします。特別な構築手順は不要です。

## ライセンス

このプロジェクトはMITライセンスの下で公開されています。
