# أدواتي | ADAWATI

المصدر الكامل لموقع **أدواتي**، جاهز للرفع إلى مستودع GitHub وربطه مباشرةً بمنصة Vercel.

## الرفع إلى GitHub

1. أنشئ مستودعًا جديدًا وفارغًا في GitHub.
2. فك ضغط الحزمة وارفع **محتويات المجلد نفسها** إلى جذر المستودع.
3. لا ترفع ملفات `.env` أو أي مفاتيح سرية.
4. فحص GitHub Actions سيشغّل TypeScript وبناء Next.js تلقائيًا بعد كل رفع.

## الربط مع Vercel

استورد مستودع GitHub من لوحة Vercel واستخدم الإعدادات المرفقة في `vercel.json`:

- Framework: `Next.js`
- Install Command: `npm ci --include=dev`
- Build Command: `npm run vercel-build`
- Node.js: `24.x`

أضف المتغيرات التالية في إعدادات Vercel للبيئات Production وPreview وDevelopment:

- `SUPABASE_URL`
- `SUPABASE_PUBLISHABLE_KEY`
- `MINJAZ_DB_TOKEN` — متغير سري يُستخدم على الخادم فقط

## التشغيل المحلي

```bash
npm ci --include=dev
npm run dev
```

ثم افتح `http://localhost:3000`.

## التحقق

```bash
npm run typecheck
npm run build
```

> ملاحظة: هذه الحزمة مناسبة لمستودع GitHub مع نشر Vercel. لا تستخدم GitHub Pages للموقع الكامل؛ لأنه يتضمن Next.js وواجهات API ووظائف خادمية لا تعمل على الاستضافة الثابتة وحدها.
