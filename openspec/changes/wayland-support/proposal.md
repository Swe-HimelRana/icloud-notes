## Why
Electronアプリである `icloud-notes` をLinuxのWayland環境でネイティブに動作させ、HiDPI環境でのスケーリング改善、パフォーマンス向上、および最新のデスクトップ環境への適合を図ります。現状、X11経由（XWayland）で動作することが多く、表示がぼやけるなどの課題があります。

## What Changes
- `main.js` にて起動時に Wayland を自動検知・有効化するための Ozone プラットフォームフラグを設定します。
- `package.json` の `snap` 設定に `wayland` プロトコルへのアクセス権限を追加します。

## Capabilities

### New Capabilities
- `wayland-native-support`: LinuxにおけるWaylandネイティブサポートの要件。これには、ディスプレイプロトコルの自動検知と適切なフォールバック、およびWayland環境特有の挙動（IMEなど）への配慮が含まれます。

### Modified Capabilities
- なし

## Impact
- `main.js`: 起動シーケンスの初期段階でのコマンドラインフラグ追加。
- `package.json`: Snapパッケージの権限（plugs）の拡張。
- Linux ユーザーエクスペリエンス: 高解像度ディスプレイでの表示品質向上、入力の安定性。
