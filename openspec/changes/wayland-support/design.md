## Context

`icloud-notes` は Electron 30 をベースにしたデスクトップアプリですが、Linux環境ではデフォルトで XWayland (X11互換レイヤー) を介して動作します。これにより、高解像度 (HiDPI) 環境での表示のぼやけや、入力の遅延、ウィンドウマネージャーとの不整合が生じることがあります。Electron 30 は Ozone プラットフォームを介したネイティブ Wayland サポートを備えており、これを有効化することでこれらの課題を解決します。

## Goals / Non-Goals

**Goals:**
- Linux環境において、Waylandが利用可能な場合は自動的にネイティブWaylandモードで起動する。
- Waylandが利用できない環境（X11のみ）では、引き続き正常に動作（フォールバック）する。
- Snapパッケージにおいて、Waylandプロトコルへのアクセス権限を適切に設定する。

**Non-Goals:**
- Windows/macOS 環境への影響（これらのプラットフォームでは変更を行わない）。
- 特定のWaylandコンポジター（GNOME, KDE, Swayなど）に特化した高度なチューニング。

## Decisions

### 1. Ozone プラットフォームの自動検知 (`ozone-platform=auto`)
**選択:** `enable-features=UseOzonePlatform` と `ozone-platform=auto` をコマンドラインフラグに追加する。
**理由:** `auto` を指定することで、実行環境のディスプレイサーバーをElectronが自動的に判断し、Waylandが利用可能であれば使用し、そうでなければX11にフォールバックします。これにより、単一のビルドで幅広い環境をサポートできます。

### 2. フラグの設定タイミング
**選択:** `main.js` の冒頭、`app.whenReady()` が呼び出される前（かつ他のモジュールロードの直後）に `app.commandLine.appendSwitch` を使用する。
**理由:** Chromiumのコマンドラインスイッチは、内部のブラウザプロセスが初期化される前に設定する必要があります。

### 3. Snap パッケージの権限拡張
**選択:** `package.json` の `build.snap.plugs` に `"wayland"` を追加する。
**理由:** Snap の strict confinement 下では、Wayland ソケットへのアクセスが明示的に許可されていない限り、ネイティブ Wayland 接続が拒否されます。

## Risks / Trade-offs

- **[Risk] IME (入力メソッド) の不具合** → Wayland上での日本語入力 (Fcitx/IBus) が期待通りに動作しない可能性があります。
  - **Mitigation:** 必要に応じて `app.commandLine.appendSwitch('enable-wayland-ime')` の追加を検討しますが、まずは標準の `auto` 設定で動作を確認します。
- **[Risk] ウィンドウ装飾 (Decoration) の不整合** → コンポジターによっては、ウィンドウの枠線やタイトルバーの表示が X11 時と異なる場合があります。
  - **Mitigation:** 現在の `frame: true` 設定を維持し、標準的な CSD (Client-Side Decoration) またはコンポジターによる装飾が機能することを確認します。
