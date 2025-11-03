# MyiOSApp

SwiftUIベースのシンプルなiOSアプリケーションテンプレートです。GitHub Actionsを使用した自動ビルドとリリース機能を備えています。

## 機能

- SwiftUI ベースの最新のUI実装
- iOS 15.0以降をサポート
- GitHub Actionsによる自動ビルド
- タグプッシュ時の自動リリース生成

## プロジェクト構成

```
MyiOSApp/
├── MyiOSApp/
│   ├── MyiOSAppApp.swift      # アプリケーションのエントリーポイント
│   ├── ContentView.swift       # メインビュー
│   ├── Assets.xcassets/        # アセットカタログ
│   └── Info.plist              # アプリケーション設定
└── MyiOSApp.xcodeproj/         # Xcodeプロジェクト
```

## 必要要件

- Xcode 15.0以降
- iOS 15.0以降
- macOS（ローカルビルドの場合）

## ローカルでのビルド

1. リポジトリをクローン
```bash
git clone <repository-url>
cd dev-ios
```

2. Xcodeでプロジェクトを開く
```bash
open MyiOSApp/MyiOSApp.xcodeproj
```

3. ビルドして実行
- Xcodeでスキーム "MyiOSApp" を選択
- シミュレータまたは実機を選択
- ⌘R でビルド&実行

## GitHub Actions

### 自動ビルド

`main` または `develop` ブランチへのプッシュ、および `main` へのプルリクエストで自動的にビルドが実行されます。

ワークフロー: `.github/workflows/build.yml`

### 自動リリース

バージョンタグ（`v*.*.*` 形式）をプッシュすると、自動的にリリースが作成されます。

```bash
# 例: バージョン 1.0.0 のリリースを作成
git tag v1.0.0
git push origin v1.0.0
```

ワークフロー: `.github/workflows/release.yml`

リリースには以下が含まれます:
- ビルドされたIPAファイル
- バージョン情報
- リリースノート

**注意**: このテンプレートは署名なしでビルドされます。App Storeへの配信には、適切なコード署名の設定が必要です。

## コード署名の設定（本番環境用）

App Storeやアドホック配布を行う場合は、以下の設定が必要です：

1. Apple Developer アカウントの設定
2. 証明書とプロビジョニングプロファイルの作成
3. GitHub Secretsへの証明書情報の追加
   - `CERTIFICATE_P12`: 証明書ファイル（Base64エンコード）
   - `CERTIFICATE_PASSWORD`: 証明書のパスワード
   - `PROVISIONING_PROFILE`: プロビジョニングプロファイル（Base64エンコード）

4. ワークフローファイルでの署名設定の有効化

## カスタマイズ

### アプリ名の変更

1. `MyiOSApp.xcodeproj/project.pbxproj` でPRODUCT_NAMEを変更
2. ディレクトリ名とファイル名を変更
3. Bundle Identifierを変更（`PRODUCT_BUNDLE_IDENTIFIER`）

### バンドルIDの変更

`MyiOSApp.xcodeproj/project.pbxproj` の `PRODUCT_BUNDLE_IDENTIFIER` を変更してください。

デフォルト: `com.example.MyiOSApp`

## ライセンス

MITライセンス

## 貢献

プルリクエストを歓迎します。大きな変更の場合は、まずissueを開いて変更内容を議論してください。
