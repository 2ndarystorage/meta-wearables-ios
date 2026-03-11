# Meta Wearables Device Access Toolkit for iOS

[![Swift Package](https://img.shields.io/badge/Swift_Package-0.4.0-brightgreen?logo=swift&logoColor=white)](https://github.com/facebook/meta-wearables-dat-ios/tags)
[![Docs](https://img.shields.io/badge/API_Reference-0.4-blue?logo=meta)](https://wearables.developer.meta.com/docs/reference/ios_swift/dat/0.4)

The Meta Wearables Device Access Toolkit enables developers to utilize Meta's AI glasses to build hands-free wearable experiences into their mobile applications.
By integrating this SDK, developers can reliably connect to Meta's AI glasses and leverage capabilities like video streaming and photo capture.

The Wearables Device Access Toolkit is in developer preview.
Developers can access our SDK and documentation, test on supported AI glasses, and create organizations and release channels to share with test users.
　
## 更新履歴 / Recent Changes

### 2026-03-02

#### 🆕 日本語UIサンプルの追加

`meta-wearables-dat-ios` から日本語UIを実装した3つのサンプルアプリを追加しました。

| サンプル | 概要 |
|---|---|
| **PhotoTextScan** | Meta AIグラスで撮影した写真からテキストをOCRスキャン（日本語UI） |
| **QuickCapture** | クイックフォト／ビデオキャプチャアプリ（日本語UI） |
| **QuickCaptureLite** | 軽量クイックキャプチャ＋テキスト認識オーバーレイ（日本語UI） |

#### 🎥 動画録画・保存機能の追加（CameraAccess）

`CameraAccess` サンプルに、ストリーミング映像を録画・保存する機能を追加しました。

**新機能:**
- 🔴 **録画ボタン** — ストリーミング中に録画開始／停止ボタンを表示
- 💾 **保存ダイアログ** — 録画停止後に「動画を保存しますか？」のアラートを表示
- 📱 **カメラロール保存** — 保存を選択すると写真ライブラリにMP4で保存
- 🗑 **削除オプション** — 不要な録画は破棄可能

**変更ファイル:**
- `CameraAccess/ViewModels/StreamSessionViewModel.swift` — `AVAssetWriter` による録画ロジック追加
- `CameraAccess/Extensions/UIImage+PixelBuffer.swift` — 新規作成（UIImage → CVPixelBuffer 変換）
- `CameraAccess/Views/StreamSessionView.swift` — 保存ダイアログUI追加
- `CameraAccess/Views/StreamView.swift` — 録画ボタンUI追加

---

## Documentation & Community

Find our full [developer documentation](https://wearables.developer.meta.com/docs/develop/) on the Wearables Developer Center.

You can find an overview of the Wearables Developer Center [here](https://wearables.developer.meta.com/).
Create an account to stay informed of all updates, report bugs and register your organization.
Set up a project and release channel to share your integration with test users.

For help, discussion about best practices or to suggest feature ideas visit our [discussions forum](https://github.com/facebook/meta-wearables-dat-ios/discussions).

See the [changelog](CHANGELOG.md) for the latest updates.

## Including the SDK in your project

The easiest way to add the SDK to your project is by using Swift Package Manager.

1. In Xcode, select **File** > **Add Package Dependencies...**
1. Search for `https://github.com/facebook/meta-wearables-dat-ios` in the top right corner
1. Select `meta-wearables-dat-ios`
1. Set the version to one of the [available versions](https://github.com/facebook/meta-wearables-dat-ios/tags)
1. Click **Add Package**
1. Select the target to which you want to add the packages
1. Click **Add Package**

## Developer Terms

- By using the Wearables Device Access Toolkit, you agree to our [Meta Wearables Developer Terms](https://wearables.developer.meta.com/terms),
  including our [Acceptable Use Policy](https://wearables.developer.meta.com/acceptable-use-policy).
- By enabling Meta integrations, including through this SDK, Meta may collect information about how users' Meta devices communicate with your app.
  Meta will use this information collected in accordance with our [Privacy Policy](https://www.meta.com/legal/privacy-policy/).
- You may limit Meta's access to data from users' devices by following the instructions below.

### Opting out of data collection

To configure analytics settings in your Meta Wearables DAT iOS app, you can modify your app's `Info.plist` file using either of these two methods:

**Method 1:** Using Xcode (Recommended)

1. In Xcode, select your app target in the **Project** navigator
1. Go to the **Info** tab
1. Navigate to **Custom iOS Target Properties**  and find the `MWDAT` key
1. Add a new key under `MWDAT` called `Analytics` of type `Dictionary`
1. Add a new key to the `Analytics` dictionary called `OptOut` of type `Boolean` and set the value to `YES`

**Method 2:** Direct XML editing

Add or modify the following in your `Info.plist` file.

```XML
<key>MWDAT</key>
<dict>
    <key>Analytics</key>
    <dict>
        <key>OptOut</key>
        <true/>
    </dict>
</dict>
```

**Default behavior:** If the `OptOut` key is missing or set to `NO`/`<false/>`, analytics are enabled
(i.e., you are **not** opting out). Set to `YES`/`<true/>` to disable data collection.

**Note:** In other words, this setting controls whether or not you're opting out of analytics:

- `YES`/`<true/>` = Opt out (analytics **disabled**)
- `NO`/`<false/>` = Opt in (analytics **enabled**)

## License

See the [LICENSE](LICENSE) file.

## Program Summary

- iOS SDK and sample apps for integrating Meta AI glasses with mobile apps, including device connection, camera streaming, and photo capture demos.
- Sample apps include CameraAccess/QuickCapture variants for wearables streaming and PhotoTextScan for on-device OCR from the iPhone photo library.

## How to Use

- Not verified: Open a sample in Xcode (for example `samples/CameraAccess/CameraAccess.xcodeproj` or `samples/PhotoTextScan/PhotoTextScan.xcodeproj`), set signing/bundle ID, and build/run on an iOS 17+ device.
- Not verified: For wearables streaming samples, enable Developer Mode in the Meta AI app and use a supported Meta AI glasses device; update `Info.plist` values like `MetaAppID` and `ClientToken` when required (see sample README files).

## Completion Status

- Partial: The SDK is labeled “developer preview” and the repo is primarily sample applications and integration guidance rather than a production-ready app.

## Program Summary

- iOS SDK (Swift Package) plus sample apps demonstrating Meta Wearables Device Access Toolkit integration with Meta AI glasses (device registration, streaming video, photo capture, connection states).
- Additional samples include a minimal streaming demo with filters (QuickCaptureLite) and a photo-library OCR app (PhotoTextScan) that does not require glasses.

## How to Use

- Not verified: Open a sample `*.xcodeproj` under `samples/` in Xcode, set signing/bundle ID, and build/run on an iOS 17+ device.
- Not verified: For glasses streaming samples (CameraAccess/QuickCapture/QuickCaptureLite), enable Developer Mode in the Meta AI app and update `MetaAppID`/`ClientToken` in `Info.plist` where noted; simulator is for UI only.
- Not verified: For PhotoTextScan, grant photo library access and run on device or simulator (simulator requires adding photos).

## Completion Status

- Partial (demo-quality): The SDK is still labeled developer preview, and the repo focuses on sample apps and integration flows rather than production-hardened applications.
