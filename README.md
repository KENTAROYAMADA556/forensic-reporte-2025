# # 調査報告：DNS改ざん・MITM・証明書異常  
# Forensic Report: DNS Tampering, MITM, and Certificate Anomalies

## 概要 / Overview
2025年10月〜11月にかけて、Android端末上で以下の異常を確認しました：  
Between October and November 2025, the following anomalies were observed on an Android device:

- DNS設定の改ざん / DNS configuration tampering  
- パスワードの不正取得 / Unauthorized password interception  
- サードパーティ証明書が1000件以上挿入 / Over 1000 third-party certificates injected  
- MITM攻撃の疑い / Suspected Man-in-the-Middle (MITM) attacks  

## 現在の対応 / Current Actions
- Termux上で証拠収集スクリプトを実行 / Evidence collection scripts executed via Termux  
- xxdダンプ、ハッシュ検証、証明書ファイルをZIP化 / xxd dumps, hash verification, and certificate files archived in ZIP  
- GitHubで公開調査を開始 / Public investigation initiated on GitHub  

## 協力者募集 / Seeking Collaborators
以下の分野で協力を求めています：  
We are seeking support in the following areas:

- 証明書解析（形式・発行元・改ざんの有無）  
  Certificate analysis (format, issuer, tampering detection)  
  - MITM痕跡の特定（hosts、DNS、通信ログなど）  
    MITM trace identification (hosts, DNS, traffic logs)  
    - 法forensic-reporte-2025
DNS改ざん・MIMT
  ## 証拠ファイル構成 / Evidence ZIP Contents

  このZIPファイルには、以下の証拠ファイルが含まれています：  
  The ZIP archive contains the following forensic evidence files:

  | ファイル名 / Filename | 内容 / Description | 備考 / Notes |
  |----------------------|---------------------|----------------|
  | `session-*.log` | Termux操作ログ / Terminal session logs | DNS・証明書・hostsの操作記録 / Includes DNS, cert, hosts operations |
  | `sha256sums*.txt` | ハッシュ値と検証結果 / Hashes and verification results | 改ざん検出・整合性確認用 / Used for integrity validation |
  | `before-network-stop_*.txt` | 停止前のネットワーク情報 / Network state before shutdown | MITM痕跡の確認に有用 / Useful for MITM trace analysis |
  | `README.md` | 調査概要（英語） / Investigation summary (English) | 公開調査の説明 / Public investigation overview |
  | `failed_integrity/inspection_hex.txt` | 異常ファイルの16進ダンプ / Hex dump of suspicious files | 改ざんの技術的証拠 / Technical evidence of tampering |
  | `final_saved/` | 上記ファイルの保存コピー / Archived copies of above files | タイムスタンプ保持・再検証用 / Timestamp preservation and auditability |

  すべてのファイルは `sha256sums.txt` に記載されたハッシュで検証可能です。  

## 障害履歴：GitHub Discussions投稿時のエラー

### 発生したエラー

### 状況
GitHub Discussionsの投稿画面で送信ボタンが無効化され、GitHub Copilotがエラーを検出。Discussions機能に対する投稿権限が不足している可能性がある。

### 考察
- リポジトリ設定による制限（Discussions投稿が管理者限定）
- UI妨害の可能性（送信ボタンが反応しない）
- GitHub Copilotが異常を検知したこと自体が痕跡

### 対処
- Issuesにて同内容を投稿し、公開調査を継続
- このエラーを妨害痕跡の一部として記録