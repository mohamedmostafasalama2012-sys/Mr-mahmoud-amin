# نشر بوابة متابعة الدرجات

الصفحة تعمل محليًا على هذا الجهاز بكلمة مرور `1234`. لمشاركة سجل واحد بين الموبايلات، أكمل إعداد Firebase التالي مرة واحدة:

1. أنشئ مشروعًا في [Firebase Console](https://console.firebase.google.com/) وأضف تطبيق Web.
2. انسخ `apiKey` و`authDomain` و`projectId` و`appId` إلى `FIREBASE_CONFIG` داخل `index.html`.
3. فعّل Email/Password من Authentication، وأنشئ حسابًا للمدرس.
4. أنشئ قاعدة Firestore في وضع Production.
5. ثبّت Node.js LTS، ثم ثبّت Firebase CLI من PowerShell:

   ```powershell
   npm install -g firebase-tools
   firebase login
   firebase use --add
   firebase deploy --only hosting,firestore:rules
   ```

6. من قائمة Authentication انسخ UID حساب المدرس. في Firestore أنشئ مجموعة `admins`، ثم مستندًا يكون معرّفه هو UID، وأضف الحقل `enabled` بقيمة `true`.
7. افتح رابط Hosting الناتج من Firebase. سجّل دخول الأدمن بالبريد وكلمة المرور، وأضف الطلاب. لكل طالب سينشأ كود وصول عشوائي؛ أرسل الرابط والكود لولي الأمر عبر واتساب. ولي الأمر يحتاج الاسم والكود معًا.

قواعد Firestore تمنع استعراض قائمة الطلاب للعامة. قراءة سجل واحد تتطلب كود الوصول العشوائي الخاص به، والكتابة تتطلب حساب أدمن مفعّلًا. لا تشارك كلمة مرور حساب المدرس.

السجلات الموجودة في التخزين المحلي لا تُرفع تلقائيًا إلى Firebase. بعد النشر، أضفها من لوحة الأدمن؛ سيظل التخزين المحلي القديم موجودًا على الجهاز، لكنه لن يظهر في الرابط المشترك.
