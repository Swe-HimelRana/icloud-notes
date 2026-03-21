## 1. アプリケーション層の修正 (main.js)

- [ ] 1.1 `main.js` の冒頭に Linux 環境判定を追加する
- [ ] 1.2 `app.commandLine.appendSwitch('enable-features', 'UseOzonePlatform')` を追加する
- [ ] 1.3 `app.commandLine.appendSwitch('ozone-platform', 'auto')` を追加する

## 2. パッケージング設定の更新 (package.json)

- [ ] 2.1 `package.json` の `build.snap.plugs` セクションを確認する
- [ ] 2.2 `plugs` リストに `"wayland"` を追加する

## 3. 動作確認と検証

- [ ] 3.1 Wayland 環境（GNOME等）で起動し、ネイティブモードで動作することを確認する
- [ ] 3.2 X11 環境で起動し、正常にフォールバックすることを確認する
- [ ] 3.3 HiDPI 環境での表示がぼやけないことを確認する
