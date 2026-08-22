# أدواتي | ADAWATI

منصة أدوات عربية مبنية باستخدام Next.js ومهيأة للنشر على Cloudflare Workers
عبر OpenNext. هذه الحزمة هي **سورس كامل**: الصفحات وواجهات API والأصول
والاختبارات وإعدادات GitHub Actions وCloudflare موجودة في جذر المشروع.

> مهم: يجب أن يظهر مجلد `app` في GitHub بجانب `package.json`. رفع ملفات الجذر
> وحدها سيؤدي إلى خطأ Cloudflare: `Couldn't find any pages or app directory`.

## المتطلبات

- Node.js 24
- npm
- حساب Cloudflare Workers للنشر
- متغيرات Supabase للرسائل والتحليلات ولوحة الإدارة

## التشغيل المحلي

```bash
npm ci
npm run dev
```

## الفحص والبناء

```bash
npm run validate
```

يشغّل هذا الأمر ESLint وTypeScript والاختبارات وبناء Next.js وبناء OpenNext
ثم يفحص حزمة Worker محليًا بدون نشرها.

## النشر على Cloudflare

إعدادات Cloudflare الأساسية موجودة في:

- `wrangler.jsonc`
- `open-next.config.ts`
- `CLOUDFLARE-DEPLOY.md`

للنشر من جهاز موثق بحساب Cloudflare:

```bash
npm run deploy
```

وللنشر التلقائي من GitHub، اتبع الخطوات الموجودة في
[`CLOUDFLARE-DEPLOY.md`](./CLOUDFLARE-DEPLOY.md).

لرفع المشروع للمرة الأولى إلى GitHub، اتبع
[`UPLOAD-TO-GITHUB.md`](./UPLOAD-TO-GITHUB.md).

## متغيرات البيئة

انسخ أسماء المتغيرات من `.env.example`. لا ترفع `.env` أو `.dev.vars` ولا أي
مفتاح سري إلى GitHub.

- `NEXT_PUBLIC_SITE_URL`
- `SUPABASE_URL`
- `SUPABASE_PUBLISHABLE_KEY`
- `MINJAZ_DB_TOKEN`

## Vercel

ما زال `vercel.json` وسكربت `vercel-build` موجودين للحفاظ على إمكانية النشر على
Vercel، لكن إعداد النشر الأساسي في هذا المستودع هو Cloudflare Workers.
