# Double Voice Explorer

*[English](README.md) | 日本語*

植民地時代のラゴス新聞（1882-1921年）における感情パターンと「ダブルボイス」現象を分析するWebベースのツール

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## クイックスタート

1. **ツールを開く**:
    * **オンライン（推奨）**: [ライブデモ](https://nozomi-sawada.github.io/double-voice-explorer/)にアクセス
    * **オフライン / ローカル（再現性の確保）**:
        1. 以下の**3つの必須ファイル**をコンピュータの**同じフォルダ**にダウンロードしてください：
            * **`index.html`**
            * **`chart.min.js`**
            * **`papaparse.min.js`**
        2. ダウンロードした`index.html`ファイルをブラウザで開きます。
            (*これにより、外部依存関係のない安全な環境でツールを実行できます。*)

2. **データの読み込み**: 感情分析結果を含むCSVファイルをアップロード、またはサンプルデータを使用
3. **分析**: 感情ペアを選択し、しきい値を調整して、可視化を探索
4. **エクスポート**: さらなる統計分析のために結果をダウンロード

### データ形式
```csv
id,year,PublicationDate,Trust,Fear,Sadness,Anticipation,Joy,Disgust,Surprise,Anger,data_source,article_type
```
感情値は正規化されている必要があります（0-1スケール）。

## 研究背景

このデジタルヒューマニティーズツールは、植民地時代のアフリカ新聞における事前計算された感情パターンを可視化・分析します。本プロジェクトは、ラゴスの2つの主要な出版物、*Lagos Observer*（1882-1888年）と*Lagos Weekly Record*（1891-1921年）を調査し、計算テキストマイニング手法を通じて社説と読者投稿を比較します。

植民地時代の新聞は、同一テキスト内に複雑で矛盾する感情を含むことが多く、感情分析に独特の課題をもたらします。「ダブルボイス」現象とは、希望と絶望、信頼と疑念など、相反する感情が同時に存在することを指し、植民地経験の複雑な感情的風景を反映しています。本ツールは、これらの共存する感情状態を特定・分析するための専門的なメトリクスと可視化を提供し、植民地時代のアフリカ新聞研究における計算手法に貢献します。

## 機能

- **インタラクティブな可視化**: Chart.jsを使用した散布図と時系列分析
- **4カテゴリー比較**: 社説 vs 読者投稿 × Lagos Observer vs Lagos Weekly Record
- **複数のメトリクス**:
  - ダブルボイススコア: √(感情₁ × 感情₂)
  - 感情バランス: 1 - |感情₁ - 感情₂|
  - 感情強度: (感情₁ + 感情₂) / 2
- **エクスポート機能**: 統計分析用のCSVダウンロード
- **インストール不要**: 純粋なHTML/CSS/JavaScript、ブラウザで動作

## 技術詳細

- **フロントエンド**: HTML/CSS/JavaScript（ビルドプロセス不要）
- **可視化**: Chart.js 3.9.1（ローカルライブラリ）
- **データ処理**: Papa Parse 5.3.0（ローカルライブラリ）
- **デプロイ**: GitHub Pages

## セキュリティと再現性

このツールは、包括的なセキュリティレビューに基づき、セキュリティと長期的な学術的再現性を強く重視して設計されました。

1. **セキュリティ**:
   * **XSS防止**: すべての`.innerHTML`操作は、ユーザーアップロードデータからのDOM-based XSS攻撃を防ぐため、安全な`.textContent`メソッドに置き換えられました。
   * **CSVフォーミュラインジェクション**: すべてのエクスポート文字列データは、スプレッドシートソフトウェアでの悪意のあるフォーミュラ実行を防ぐため、`sanitizeForCSV()`でサニタイズされます。
   * **イベントハンドラー**: すべてのインライン`onclick`属性は削除され、安全な`addEventListener`メソッドに置き換えられました。

2. **再現性**:
   * **ローカルライブラリ**: このツールは、外部CDNを使用する代わりに、**意図的に`Chart.js`と`Papa Parse`のローカルコピー**（`./chart.min.js`、`./papaparse.min.js`）をバンドルしています。
   * **理由**: このアプローチは、長期的な機能性を保証し（CDNが変更された場合でも）、オフライン環境やSRI検証をブロックする可能性のあるネットワーク（プロキシなど）でもツールが動作することを保証します。
   * **タイムスタンプ**: エクスポートされたファイル名は、研究データのタイムゾーンの曖昧さを防ぐため、ユーザーのローカル日付（`localDateStamp()`）を使用します。

## サンプルデータ

- `sample_lo_editorial.csv`: Lagos Observer社説コンテンツ
- `sample_lo_correspondence.csv`: Lagos Observer読者投稿
- `sample_lwr_editorial.csv`: Lagos Weekly Record社説コンテンツ

## 研究への応用

- **植民地研究**: 感情労働と抵抗戦略の分析
- **デジタルヒューマニティーズ**: 歴史的新聞分析への計算的アプローチ
- **アフリカ研究**: 初期アフリカのジャーナリズムと公共圏の形成

## 開発に関する謝辞

このツールは澤田望によって開発されました。このリポジトリの一部は、コード実装とデバッグのためにAI支援（例：Claude Code Sonnet 4.5、Gemini 2.5 Pro、GPT-5 Thinking）で草案されました。すべての学術コンテンツ、方法論的決定、および検証は人間の研究者によってレビューされ、その責任は人間の研究者のみに帰属します。

## 引用

```bibtex
@software{sawada2025doublevoice,
  author = {Sawada, Nozomi},
  title = {Double Voice Explorer: Analyzing Emotional Patterns in Colonial Lagos Newspapers (1882-1921)},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/nozomi-sawada/double-voice-explorer}
}
```

## ライセンス

MITライセンス - 詳細は[LICENSE](LICENSE)ファイルを参照してください。

## 連絡先

**澤田 望**
GitHub: [@nozomi-sawada](https://github.com/nozomi-sawada)
