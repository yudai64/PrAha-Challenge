### 課題1
[こちら参照](https://github.com/yudai64/react-tutorial)

### 課題2

***ビジュアルリグレッションテスト***
- メリット
    - 変更が画像で表示されるので直感的でわかりやすい
    - レンダリングされない要素の変更(今回で言うと色の変更)も検出される
- デメリット
    - 見た目に表れない HTML attributes が確認できない
    - テストの数が多いと時間がかかる?(想像です)

***スナップショットテスト***

- メリット
    - 見た目に表れない HTML attributes を確認できる
- デメリット
    - 差分がどう画面に影響しているかがわかりにくい(差分が多いほどよりわからない)
    - レンダリングされない要素の変更は検出されない


### 課題3
- imageSnapShot()の引数であるbeforeScreenshotを以下のように設定している場合、どのような問題を解決できそうしょうか。
```
const beforeScreenshot = (page, { context: { kind, story }, url }) => {
  return new Promise((resolve) =>
    setTimeout(() => {
      resolve();
    }, 600)
  );
};
```

---
### 参考
- [storyshots-puppeteer](https://github.com/storybookjs/storybook/tree/master/addons/storyshots/storyshots-puppeteer)
- [Cannot find module 'puppeteer-core/internal/common/Device.js'](https://stackoverflow.com/questions/74078944/cannot-find-module-puppeteer-core-internal-common-device-js)
- [storybookのVRTでjest-image-snapshotを試す](https://zenn.dev/wintyo/articles/ee8c7926336460)

- [ABEMAでスナップショットテストをやめてVisual Regression Testingに移行する話](https://developers.cyberagent.co.jp/blog/archives/29784/)