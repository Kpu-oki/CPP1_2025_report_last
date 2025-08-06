提出用リポジトリです。
# このソースコードでの運用、利用は推奨しません!


# クイックスタート
1. **リポジトリを clone / download**

2. `public/フォルダに  
   **`firebase-config.js` として新たにファイルを作成し、Firebase Console で取得した  
   `apiKey / projectId / appId …` を入力してください。

   ```js
   // public/firebase-config.js
   export const firebaseConfig = {
     apiKey:            "YOUR_API_KEY",
     authDomain:        "YOUR_PROJECT.firebaseapp.com",
     projectId:         "YOUR_PROJECT",
     storageBucket:     "YOUR_PROJECT.appspot.com",
     messagingSenderId: "XXXX",
     appId:             "1:XXXX:web:XXXXXXXX"
   };
   ```

   -----
   3.Firebase Console で設定

    Authentication → 匿名ログイン を有効化

    Firestore → ルール を下記に貼り付けて公開

   ```JS
   rules_version = '2';
   service cloud.firestore {
   match /databases/{db}/documents {
   match /{doc=**} {
      // 匿名を含む「認証済みユーザー」のみ可
      allow read, write: if request.auth != null;
    }
   }}
```


