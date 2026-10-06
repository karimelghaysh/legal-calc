# تحويل الحاسبة إلى تطبيق أندرويد (APK)

## الطريقة الأسهل: بناء تلقائي على GitHub (بدون تثبيت أي برنامج)
1. أنشئ حسابًا مجانيًا على github.com ثم أنشئ مستودعًا جديدًا (New repository) باسم مثل `legal-calc`.
2. ارفع كل محتويات هذا المجلد إلى المستودع (زر Add file ← Upload files). تأكد أن المجلد المخفي `.github` ارفع معه.
3. افتح تبويب **Actions** ← اختر **Build Android APK** ← **Run workflow**.
4. بعد 5–8 دقائق افتح العملية المكتملة ونزّل الملف `karim-legal-calculator-apk` من قسم Artifacts، وبداخله `app-debug.apk`.
5. انقل الملف إلى هاتفك وثبّته (فعّل «التثبيت من مصادر غير معروفة» عند الطلب).

## طريقة بديلة: على جهازك
يلزم Node.js 20 وJDK 17 وAndroid Studio:
```
npm install
npx cap add android
npx cap sync android
npx cap open android      # ثم Build ← Build APK(s)
```

## ملاحظات
- ملف الصفحة الأساسي: `www/index.html`. أي تعديل عليه ثم إعادة البناء ينعكس على التطبيق.
- ملف APK الناتج «debug» مناسب للاستخدام الشخصي. للنشر على Google Play يلزم توقيع إصدار release وحساب مطوّر.
- لتغيير اسم التطبيق أو المعرّف عدّل `capacitor.config.json` (`appName` و`appId`).
- يعمل التطبيق بدون إنترنت، عدا خط Tajawal الذي يتطلب اتصالًا ويُستبدل بخط النظام عند عدم توفره.
- الملفان `manifest.json` و`sw.js` يتيحان أيضًا تثبيت الصفحة كتطبيق ويب (PWA) إذا استضفتها على GitHub Pages.
