# رفع النسخة الكاملة إلى GitHub

## الطريقة الموصى بها

1. فك ضغط الحزمة الكاملة على جهازك.
2. افتح مستودع `mahmoodalhamdani/ADAWATI` في GitHub Desktop أو استنسخه محليًا.
3. انسخ **محتويات الحزمة** إلى جذر المستودع، وليس المجلد الحاوي لها.
4. نفّذ commit ثم push إلى فرع `main`.

## فحص سريع قبل Cloudflare

يجب أن تظهر العناصر التالية معًا في الصفحة الرئيسية للمستودع:

- `app/`
- `lib/`
- `public/`
- `tests/`
- `package.json`
- `package-lock.json`
- `wrangler.jsonc`
- `open-next.config.ts`

لا ترفع هذه المجلدات حتى لو كانت موجودة على جهازك:

- `node_modules/`
- `.next/`
- `.open-next/`
- `.wrangler/`

ولا ترفع ملفات `.env` أو `.dev.vars` أو أي مفاتيح سرية.
