# CLAUDE.md

**Language / 言語**: [English](#english) | [日本語](#日本語)

---

<a id="english"></a>
## English

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Double Voice Explorer is a single-file HTML web application for analyzing emotional patterns and "Double Voice" phenomena in colonial Lagos newspapers (1882-1921). It's a standalone visualization tool that runs entirely in the browser with no build process or server requirements.

## Key Commands

### Local Development
```bash
# Simply open the HTML file in any modern browser
open index.html
# or navigate to file in browser

# For GitHub Pages deployment
git add .
git commit -m "Update application"
git push origin main
```

### File Preparation for GitHub
```bash
# Files are already renamed to GitHub standards:
# index.html (main application)
# LICENSE (license file) 
# .gitignore (git ignore rules)
# README.md (documentation)

# Create sample data directory
mkdir sample-data
mv lwr-editorial-sample.txt sample-data/sample_lwr_editorial.csv
```

## Application Architecture

### Core Technologies
- **Pure HTML/CSS/JavaScript**: No build process, framework, or dependencies
- **Chart.js 3.9.1 (local library)**: Interactive scatter plots and time series visualizations
- **Papa Parse 5.3.0 (local library)**: Client-side CSV file parsing
- **Responsive Design**: Mobile and tablet compatible

### Data Processing Pipeline
1. **CSV Upload**: Users upload emotion analysis data files
2. **Automatic Detection**: Recognizes Lagos Observer (LO) vs Lagos Weekly Record (LWR) data
3. **Real-time Analysis**: Calculates Double Voice metrics on-the-fly
4. **Interactive Visualization**: Updates charts based on user filters
5. **Export Functionality**: Downloads processed results as CSV

### Double Voice Metrics
- **DV Score (Geometric Mean)**: √(Emotion1 × Emotion2) - synergistic strength
- **Balance**: 1 - |Emotion1 - Emotion2| - emotional equilibrium
- **Intensity**: (Emotion1 + Emotion2) / 2 - average emotional strength
- **Valid DV**: Boolean flag when both emotions exceed threshold (default 0.5)

### Security Features
- **XSS Prevention**: All DOM manipulation uses safe methods (`.textContent`, `createElement()`, `appendChild()`)
- **CSV Injection Protection**: Exported data is sanitized via `sanitizeForCSV()` to prevent formula execution in spreadsheet software
- **Event Handler Security**: No inline event handlers (`onclick`), all use `addEventListener()`
- **Local Libraries**: Chart.js and Papa Parse are bundled locally (`./chart.min.js`, `./papaparse.min.js`) to ensure reproducibility and avoid network tampering

## Data Format Requirements

### Required CSV Columns
- `id`: Unique article identifier
- `year` or `Year`: Publication year (1882-1921)
- Emotion columns: `Trust`, `Disgust`, `Joy`, `Sadness`, `Fear`, `Anger`, `Anticipation`, `Surprise` (values 0-1)

### Supported Emotion Pairs
- Trust ↔ Disgust (default)
- Joy ↔ Sadness
- Anticipation ↔ Surprise
- Anger ↔ Fear

## Deployment Strategy

### GitHub Pages Setup
1. Repository must contain `index.html` as main file
2. Enable GitHub Pages in repository settings
3. Application will be available at `https://username.github.io/repository-name/`

### Single-File Architecture Benefits
- No build process required
- Easy deployment and sharing
- Self-contained with local library dependencies (no external CDNs)
- Works offline and in restrictive network environments

## Research Context

This tool analyzes emotional expression in colonial African newspapers, specifically:
- **Lagos Observer** (1882-1888): Editorials and correspondence
- **Lagos Weekly Record** (1891-1921): Editorial content
- **4-Category Analysis**: Editorial vs Correspondence × LO vs LWR comparison
- **Double Voice Theory**: Based on W.E.B. Du Bois's double consciousness concept

## Development Notes

### Code Organization
The application follows a single-file structure with clearly separated sections:
- CSS styling (responsive design with gradient themes)
- HTML structure (upload interface, controls, visualization containers)
- JavaScript modules (data processing, visualization, export functionality)

### Key JavaScript Functions
- `loadCSVData()`: Handles file upload and parsing
- `calculateDoubleVoice()`: Computes DV metrics with explicit type conversion and NaN handling
- `updateAnalysis()`: Refreshes visualizations based on filters with input validation
- `compareEditorialReader()`: Launches 4-category comparison mode
- `exportResults()`: Downloads analysis results

### Performance and Input Validation Patterns

**Chart Update Strategy**:
All chart update functions (`updateScatterPlot()`, `updateTimeSeries()`, `updateComparisonBarChart()`, `updateDistributionChart()`) follow this pattern:
- **First render**: Create new Chart instance
- **Subsequent updates**: Use `chart.update()` instead of `chart.destroy()` + `new Chart()`
- **Benefits**: Eliminates flickering, improves rendering speed, reduces memory churn

**Input Validation**:
- `calculateDoubleVoice()`: Uses `parseFloat(value) || 0` for emotion values to handle NaN/undefined
- `updateAnalysis()`: Validates threshold and year inputs with fallback defaults:
  - Threshold: Defaults to 0.5 if invalid
  - Year range: Falls back to input min/max attributes, then to 1882-1921 if still invalid
- **Pattern**: `isNaN()` checks combined with logical OR (`||`) for default values

**Year Display Formatting**:
- Time series charts use `ticks: { useGrouping: false }` to prevent comma separators (e.g., "1887" not "1,887")
- Tooltip callbacks explicitly remove commas: `context[0].label.replace(/,/g, '')`

### Customization Points
- Emotion pair definitions can be extended
- Threshold ranges are configurable
- Chart styling follows Chart.js theming
- Export formats can be modified

## Academic Usage

The tool supports digital humanities research with:
- Citation format provided in README
- Exportable results for statistical analysis
- Configurable thresholds for different research questions
- Time series analysis for historical progression

---

<a id="日本語"></a>
## 日本語

このファイルは、Claude Code (claude.ai/code) がこのリポジトリのコードを操作する際のガイダンスを提供します。

## プロジェクト概要

Double Voice Explorerは、植民地時代のラゴス新聞（1882-1921年）における感情パターンと「ダブルボイス」現象を分析するための単一ファイルHTMLウェブアプリケーションです。ビルドプロセスやサーバー要件なしでブラウザ上で完全に動作するスタンドアロンの可視化ツールです。

## 主要なコマンド

### ローカル開発
```bash
# 任意のモダンブラウザでHTMLファイルを開く
open index.html
# またはブラウザでファイルに移動

# GitHub Pagesデプロイメント用
git add .
git commit -m "Update application"
git push origin main
```

### GitHubファイル準備
```bash
# ファイルはすでにGitHub標準にリネーム済み:
# index.html (メインアプリケーション)
# LICENSE (ライセンスファイル)
# .gitignore (git無視ルール)
# README.md (ドキュメント)

# サンプルデータディレクトリを作成
mkdir sample-data
mv lwr-editorial-sample.txt sample-data/sample_lwr_editorial.csv
```

## アプリケーションアーキテクチャ

### コア技術
- **Pure HTML/CSS/JavaScript**: ビルドプロセス、フレームワーク、依存関係なし
- **Chart.js 3.9.1 (ローカルライブラリ)**: インタラクティブな散布図と時系列可視化
- **Papa Parse 5.3.0 (ローカルライブラリ)**: クライアントサイドCSVファイル解析
- **レスポンシブデザイン**: モバイルおよびタブレット対応

### データ処理パイプライン
1. **CSVアップロード**: ユーザーが感情分析データファイルをアップロード
2. **自動検出**: Lagos Observer (LO) と Lagos Weekly Record (LWR) のデータを認識
3. **リアルタイム分析**: Double Voiceメトリクスをその場で計算
4. **インタラクティブ可視化**: ユーザーフィルターに基づいてチャートを更新
5. **エクスポート機能**: 処理結果をCSVとしてダウンロード

### Double Voiceメトリクス
- **DVスコア（幾何平均）**: √(感情1 × 感情2) - 相乗的強度
- **バランス**: 1 - |感情1 - 感情2| - 感情の均衡
- **強度**: (感情1 + 感情2) / 2 - 平均感情強度
- **有効DV**: 両方の感情が閾値を超えた場合のブール値フラグ（デフォルト0.5）

### セキュリティ機能
- **XSS防止**: すべてのDOM操作は安全なメソッド（`.textContent`、`createElement()`、`appendChild()`）を使用
- **CSVインジェクション保護**: エクスポートされたデータは`sanitizeForCSV()`でサニタイズされ、スプレッドシートソフトウェアでの数式実行を防止
- **イベントハンドラーセキュリティ**: インラインイベントハンドラー（`onclick`）は使用せず、すべて`addEventListener()`を使用
- **ローカルライブラリ**: Chart.jsとPapa Parseはローカルにバンドル（`./chart.min.js`、`./papaparse.min.js`）され、再現性を確保しネットワーク改ざんを回避

## データフォーマット要件

### 必須CSVカラム
- `id`: 一意の記事識別子
- `year` または `Year`: 発行年（1882-1921）
- 感情カラム: `Trust`, `Disgust`, `Joy`, `Sadness`, `Fear`, `Anger`, `Anticipation`, `Surprise`（値は0-1）

### サポートされている感情ペア
- Trust ↔ Disgust（デフォルト）
- Joy ↔ Sadness
- Anticipation ↔ Surprise
- Anger ↔ Fear

## デプロイメント戦略

### GitHub Pagesセットアップ
1. リポジトリにメインファイルとして`index.html`が必要
2. リポジトリ設定でGitHub Pagesを有効化
3. アプリケーションは`https://username.github.io/repository-name/`で利用可能

### 単一ファイルアーキテクチャの利点
- ビルドプロセス不要
- 簡単なデプロイメントと共有
- ローカルライブラリ依存関係で自己完結（外部CDN不使用）
- オフラインおよび制限的なネットワーク環境で動作

## 研究コンテキスト

このツールは、植民地アフリカ新聞における感情表現を分析します。具体的には：
- **Lagos Observer**（1882-1888年）: 社説と通信
- **Lagos Weekly Record**（1891-1921年）: 社説コンテンツ
- **4カテゴリー分析**: 社説 vs 通信 × LO vs LWRの比較
- **Double Voice理論**: W.E.B. デュボイスの二重意識概念に基づく

## 開発ノート

### コード構成
アプリケーションは明確に分離されたセクションを持つ単一ファイル構造に従います：
- CSSスタイリング（グラデーションテーマを使用したレスポンシブデザイン）
- HTML構造（アップロードインターフェース、コントロール、可視化コンテナ）
- JavaScriptモジュール（データ処理、可視化、エクスポート機能）

### 主要なJavaScript関数
- `loadCSVData()`: ファイルアップロードと解析を処理
- `calculateDoubleVoice()`: 明示的な型変換とNaN処理を使用してDVメトリクスを計算
- `updateAnalysis()`: 入力検証を伴うフィルターに基づいて可視化を更新
- `compareEditorialReader()`: 4カテゴリー比較モードを起動
- `exportResults()`: 分析結果をダウンロード

### パフォーマンスと入力検証パターン

**チャート更新戦略**:
すべてのチャート更新関数（`updateScatterPlot()`、`updateTimeSeries()`、`updateComparisonBarChart()`、`updateDistributionChart()`）は次のパターンに従います：
- **初回レンダリング**: 新しいChartインスタンスを作成
- **その後の更新**: `chart.destroy()` + `new Chart()`の代わりに`chart.update()`を使用
- **利点**: ちらつきを排除し、レンダリング速度を向上させ、メモリチャーンを削減

**入力検証**:
- `calculateDoubleVoice()`: NaN/undefinedを処理するために感情値に`parseFloat(value) || 0`を使用
- `updateAnalysis()`: フォールバックデフォルトで閾値と年の入力を検証：
  - 閾値: 無効な場合は0.5にデフォルト
  - 年範囲: input要素のmin/max属性にフォールバック、それでも無効な場合は1882-1921にフォールバック
- **パターン**: デフォルト値のための論理OR（`||`）と組み合わせた`isNaN()`チェック

**年表示フォーマット**:
- 時系列チャートは`ticks: { useGrouping: false }`を使用してカンマ区切りを防止（例：「1,887」ではなく「1887」）
- ツールチップコールバックは明示的にカンマを削除: `context[0].label.replace(/,/g, '')`

### カスタマイズポイント
- 感情ペア定義は拡張可能
- 閾値範囲は設定可能
- チャートスタイリングはChart.jsテーマに従う
- エクスポート形式は変更可能

## 学術的使用

このツールは以下でデジタルヒューマニティーズ研究をサポートします：
- READMEで提供される引用形式
- 統計分析用のエクスポート可能な結果
- 異なる研究課題のための設定可能な閾値
- 歴史的進行のための時系列分析