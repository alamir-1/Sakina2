# Sakina — تحويل إلى APK أندرويد

## المتطلبات على جهازك
- Node.js (من https://nodejs.org — نسخة LTS)
- Android Studio (من https://developer.android.com/studio)
- JDK 17

---

## الخطوات بالترتيب

### 1. فك الضغط وادخل المجلد
```
cd sakina-app
```

### 2. تثبيت الباكدجات
```
npm install
```

### 3. إضافة منصة أندرويد
```
npx cap add android
```

### 4. مزامنة الملفات
```
npx cap sync android
```

### 5. افتح في Android Studio
```
npx cap open android
```
من Android Studio: Build → Build Bundle(s)/APK(s) → Build APK(s)

### أو مباشرة من Terminal
```
cd android
./gradlew assembleDebug
```

### مكان الـ APK
```
android/app/build/outputs/apk/debug/app-debug.apk
```

---

## ملاحظات خاصة بمشروع Sakina

### ✅ ما يعمل تلقائياً
- Firebase Auth + Realtime Database (كلها HTTPS)
- كل مكتبات Firebase SDK عبر CDN
- خرائط Google (window.open → Google Maps)

### ⚠️ تحتاج انتباه
1. **window.open للخرائط**: عند الضغط على اتجاهات المسجد، سيفتح Google Maps
   في متصفح خارجي — هذا سلوك طبيعي في Capacitor
   (يمكن تحسينه لاحقاً بـ @capacitor/browser plugin)

2. **Firebase Security Rules**: تأكد أن rules مضبوطة
   في Firebase Console → Realtime Database → Rules

3. **الإنترنت مطلوب**: التطبيق يعتمد على Firebase وبيانات أونلاين

---

## متغيرات البيئة (ANDROID_HOME)
### Windows:
```
ANDROID_HOME = C:\Users\<YourName>\AppData\Local\Android\Sdk
PATH += %ANDROID_HOME%\platform-tools
```
### Mac/Linux (~/.zshrc):
```
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/platform-tools
```
