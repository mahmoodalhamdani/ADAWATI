# نشر أدواتي على Cloudflare Workers

المشروع مهيأ لتشغيل Next.js عبر محول OpenNext الرسمي، واسم الـWorker في
`wrangler.jsonc` هو `adawati` ليطابق المشروع الحالي في لوحة Cloudflare.

## ربط المستودع بالـWorker الحالي

1. افتح **Workers & Pages** في لوحة Cloudflare.
2. افتح Worker باسم **adawati**.
3. انتقل إلى **Settings → Builds** واضغط **Connect**.
4. اختر مستودع `mahmoodalhamdani/ADAWATI` والفرع `main`.
5. استخدم الإعدادات التالية:

| الإعداد | القيمة |
| --- | --- |
| Root directory | `/` |
| Build command | `npm run cf:build` |
| Deploy command | `npx wrangler deploy` |
| Non-production deploy command | `npx wrangler versions upload` |

## المتغيرات المطلوبة

أضف القيم نفسها في **Build Variables and Secrets** وفي متغيرات Worker وقت
التشغيل. لا تضع القيم السرية داخل GitHub.

| المتغير | النوع |
| --- | --- |
| `NEXT_PUBLIC_SITE_URL` | Variable: `https://adawati.adawati.workers.dev` |
| `SUPABASE_URL` | Variable |
| `SUPABASE_PUBLISHABLE_KEY` | Secret |
| `MINJAZ_DB_TOKEN` | Secret |

بدون متغيرات Supabase ستعمل الصفحات والأدوات المحلية، لكن الرسائل والتحليلات
وتسجيل دخول الإدارة ووظائف لوحة التحكم المرتبطة بقاعدة البيانات لن تعمل.

## التحقق المحلي

```bash
npm ci
npm run typecheck
npm run build
npm run cf:build
npm run preview
```

لا تستخدم خيار **Hello World** لإنشاء مصدر جديد؛ اربط هذا المستودع بالـWorker
الحالي حتى يستبدل النشر الجديد القالب التجريبي.
