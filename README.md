# Private Tab Beam - Web Viewer

PC の Chrome シークレットウィンドウから転送されたタブ一覧を、iPhone/iPad 等のモバイル Safari（プライベートブラウズ）上でローカル復号・表示するための静的Webビューアです。

## 特徴とセキュリティ設計
- **完全ゼロ外部通信**: 外部API通信、分析タグ、CDN参照を一切排除。厳格な Content Security Policy (CSP) により外部リクエストを遮断しています。
- **アカウント・中継サーバ不要**: データはすべて QR コード経由でブラウザの URL ハッシュ（`#` 以降）として渡されます。URL ハッシュはサーバーへ送信されないため、アクセスログ等にも一切残りません。
- **端末内ローカル復号**: ブラウザ標準の Web Stream API (`DecompressionStream('deflate-raw')`) を使用して端末ローカルで高速に解凍・復元します（iOS 16.4 以降対応）。
- **セキュア DOM 描画**: XSS 脆弱性を防ぐため、`innerHTML` を一切使用せず `textContent` のみで安全にタブ情報を描画します。

## ホスティング手順 (GitHub Pages 等)
1. 本フォルダの `index.html` を任意の静的ホスティング（例: GitHub Pages, Cloudflare Pages 等）に配置します。
2. 公開されたビューアの URL（例: `https://<username>.github.io/private-tab-beam/`）をコピーします。
3. Chrome 拡張「Private Tab Beam」の設定欄（Viewer Base URL）にその URL を貼り付けて保存します。
