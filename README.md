# AthleteCore Pro - AI姿勢分析システム

## 🏃‍♂️ プロジェクト概要

**AthleteCore Pro**は、MediaPipe Poseを活用したリアルタイムAI姿勢分析システムです。アスリートのパフォーマンス向上とヘルスケア分野でのビジネス拡大を目指すプロフェッショナル向けツールです。

### 🎯 主な機能

- **リアルタイム姿勢分析**: MediaPipeによる高精度姿勢検出
- **静的・動的解析**: 10秒カウントダウン撮影と自動録画機能
- **モバイル最適化**: スマートフォン対応のレスポンシブデザイン
- **PWA対応**: オフライン機能とアプリライクな体験
- **データ管理**: ローカルストレージによるユーザープロファイル管理

## 🔥 最新の改善事項（2025年1月18日）

### ✅ モバイルTOP画面フラッシュ問題解決

**問題**: モバイルでAthlete Welcome Screen（TOP画面）が1秒程度フラッシュしてからWelcome Pageに遷移する問題

**解決策**:
1. **HTML構造の最適化**: `#athlete-welcome`の`active`クラスを削除してJavaScript完全制御
2. **CSS初期表示制御**: 全`.app-screen`を初期非表示（`display: none !important`）に変更
3. **JavaScript初期化最適化**: 
   - `showAthleteWelcome()`を50ms後に実行（2000ms → 50ms）
   - `setupBeginAnalysisButton()`を即座に実行（遅延削除）
   - アニメーション遅延を高速化（200ms → 100ms）

**技術詳細**:
```css
/* 修正前 */
#athlete-welcome {
    display: flex !important; /* 即座に表示されフラッシュの原因 */
}

/* 修正後 */
.app-screen {
    display: none !important; /* 初期非表示 */
}
.app-screen.active {
    display: flex !important; /* JavaScript制御でのみ表示 */
}
```

### 🚀 パフォーマンス改善

- **初期化速度向上**: 2000ms → 50msの高速化
- **ボタン応答性改善**: イベントリスナーの即座設定
- **アニメーション最適化**: モバイル向けハードウェアアクセラレーション

## 📱 モバイル対応状況

### ✅ 完全対応済み
- **Begin Analysisボタン**: タッチ応答性とクリック機能
- **Manual Startボタン**: 透明グラスモーフィズム効果
- **画面遷移**: スムーズなフラッシュレス遷移
- **レスポンシブデザイン**: 各デバイスサイズ対応

### 📐 対応画面サイズ
- `max-width: 768px` - タブレット
- `max-width: 640px` - スマートフォン（縦）
- `max-width: 480px` - 小型スマートフォン
- `orientation: landscape` - 横画面最適化

## 🛠 技術スタック

### フロントエンド
- **HTML5 + CSS3**: セマンティックマークアップとモダンCSS
- **JavaScript ES6+**: 非同期処理とモダン構文
- **Tailwind CSS**: ユーティリティファーストCSS
- **MediaPipe**: Google製AI姿勢検出ライブラリ

### PWA機能
- **Service Worker**: オフライン対応とキャッシュ戦略
- **Web App Manifest**: ネイティブアプリライク体験
- **Push通知**: エンゲージメント向上（計画中）

### データ管理
- **LocalStorage**: ユーザープロファイルとセッション管理
- **RESTful Table API**: 将来的なクラウドデータ統合準備

## 🎨 デザインシステム

### Dior Sportスタイル
- **ミニマリスト美学**: 洗練されたタイポグラフィ
- **高級感演出**: カスタムアニメーション（fade-in, slide-up, geometric-float）
- **カラーパレット**: モノクロームベースの高コントラスト
- **モバイル最適化**: タッチフレンドリーなUI/UX

### アニメーション仕様
```css
@keyframes dior-fade-in {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
}

@keyframes dior-geometric-float {
    0%, 100% { transform: translateY(0px) rotate(0deg); }
    50% { transform: translateY(-10px) rotate(5deg); }
}
```

## 🏗 アーキテクチャ

### スクリーン管理システム
```javascript
// 中央集権的画面制御
function showScreen(screenId) {
    // 全画面非表示 → 対象画面表示
    // モバイル最適化済み
}
```

### 画面構成
1. **Athlete Welcome Screen** (`#athlete-welcome`) - エントランス
2. **Welcome Screen** (`#welcome`) - 登録/ログイン
3. **Registration Screen** (`#registration`) - プロファイル作成
4. **Dashboard Screen** (`#dashboard`) - メイン機能
5. **Analysis Screens** (`#static-analysis`, `#dynamic-analysis`) - 姿勢解析
6. **Results Screen** (`#results`) - 解析結果表示

## 🔧 開発環境

### ファイル構成
```
index.html                 # メインアプリケーション
service-worker.js         # PWA Service Worker  
manifest.json            # Web App Manifest
README.md               # プロジェクト文書（当ファイル）
```

### 必要な環境
- **モダンブラウザ**: Chrome 90+, Safari 14+, Firefox 88+
- **HTTPS接続**: MediaPipe Camera API要件
- **カメラアクセス**: 姿勢解析機能に必須

## 🚀 デプロイ方法

### GitHub Pages
1. リポジトリのSettingsタブを開く
2. Pagesセクションでソースを設定
3. HTTPSドメインでアクセス（カメラ機能に必須）

### ローカル開発
```bash
# HTTPSサーバーが必要（MediaPipe要件）
python -m http.server 8000
# または
npx http-server -S -p 8000
```

## 🎯 今後の開発計画

### 短期目標（1-2ヶ月）
- [ ] クラウドデータ同期機能
- [ ] 詳細解析レポート生成
- [ ] ユーザー間比較機能

### 中期目標（3-6ヶ月）
- [ ] AIコーチング機能
- [ ] ビデオ解析強化
- [ ] 企業向けダッシュボード

### 長期目標（6ヶ月+）
- [ ] ウェアラブルデバイス連携
- [ ] リアルタイム指導機能
- [ ] ヘルスケア事業展開

## 📞 サポート・連絡先

**開発者**: AI姿勢分析システム会社経営者  
**会社サイト**: https://bclab.jp  
**専門分野**: ヘルスケアビジネス、AI姿勢分析

---

**AthleteCore Pro** - プロフェッショナルアスリートと指導者のための次世代AI姿勢分析プラットフォーム 🏃‍♂️✨
