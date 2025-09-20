# 脆弱性レポート（サンプル）
- タイトル: Reflected XSS in /search
- 発見日:
- 概要:
- 影響度 (例: CVSS v3): 5.3 (中)
- 再現手順:
  1. ブラウザをBurpでプロキシに設定
  2. GET /search?q=><script>alert(1)</script>
  3. レスポンスにスクリプトが反映される
- 影響範囲:
  - ログインしているユーザのセッション窃取の可能性
- 修正案:
  - 出力時にHTMLエスケープを行う。
  - CSPの導入（Content-Security-Policy)
- 証拠（スクショ/HTTPリクエスト/レスポンス）
- 優先度・推奨対応（例: P1、即修正）