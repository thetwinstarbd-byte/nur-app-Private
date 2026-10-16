# নূর এপ: Android এপ বানানোর ধাপ

## আগে যা লাগবে
1. একটি কম্পিউটার (Windows, Mac বা Linux)
2. **Node.js** (LTS ভার্সন): https://nodejs.org
3. **Android Studio**: https://developer.android.com/studio
4. একটি Android ফোন (USB ডিবাগিং চালু) অথবা Android Studio-র এমুলেটর
5. **আজানের অডিও ফাইল** `adhan.wav` (ছোট, ১০–৩০ সেকেন্ড)। যে ফাইলের ব্যবহারের অধিকার আপনার আছে, শুধু সেটাই ব্যবহার করুন।

## ধাপ ১: প্রজেক্ট প্রস্তুত করা
এই ফোল্ডারে টার্মিনাল খুলে একে একে চালান:
```
npm install
npx cap add android
npx cap sync
```

## ধাপ ২: আজানের শব্দ বসানো
`android/app/src/main/res/` এর ভেতরে `raw` নামে ফোল্ডার বানিয়ে সেখানে `adhan.wav` রাখুন।

## ধাপ ৩: পারমিশন যোগ করা
`android/app/src/main/AndroidManifest.xml` ফাইলে `<application` লাইনের আগে এই লাইন বসান:
```
<uses-permission android:name="android.permission.SCHEDULE_EXACT_ALARM"/>
```

## ধাপ ৪: ফোনে চালানো
```
npx cap open android
```
Android Studio খুললে ফোন যুক্ত করে ▶ Run চাপুন। এপ খুলে হোমের "ওয়াক্তের রিমাইন্ডার চালু করুন" বোতাম চাপুন এবং অনুমতি দিন।

## ধাপ ৫: Play Store-এ দেওয়ার আগে
- `capacitor.config.json` এ `appId` বদলে নিজের নাম দিন (যেমন `com.yourname.nur`)
- আইকন ও স্ক্রিনশট বানান
- প্রাইভেসি পলিসি লিখুন
- Google Play Developer অ্যাকাউন্ট নিন (এককালীন ফি)
- Android Studio থেকে Signed App Bundle (.aab) বানিয়ে আপলোড করুন

## জেনে রাখুন
- এপ খুললেই পরবর্তী ৭ দিনের রিমাইন্ডার আবার সাজানো হয়। তাই অন্তত সপ্তাহে একবার এপ খুলতে হবে।
- Xiaomi, Oppo, Vivo, Realme ফোনে সেটিংসে এপকে "ব্যাটারি: Unrestricted" ও "Autostart" দিতে হয়, নইলে রিমাইন্ডার আটকে যেতে পারে।
- নামাজের সময় গণনা করা, তাই মসজিদের সময়সূচির সঙ্গে ১–২ মিনিট ফারাক হতে পারে।
