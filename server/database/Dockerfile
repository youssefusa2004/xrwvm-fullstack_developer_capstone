ADD data/dealerships.json .
ADD data/reviews.json .```

هذه الأوامر تقوم بنسخ **ملف** `dealerships.json` و**ملف** `reviews.json` إلى المجلد الرئيسي داخل الحاوية.

ولكن، في ملف `server/database/app.js`، الكود يحاول قراءة هذه الملفات من مسار مختلف:

```javascript
const reviews_data = JSON.parse(fs.readFileSync("data/reviews.json", 'utf8'));
const dealerships_data = JSON.parse(fs.readFileSync("data/dealerships.json", 'utf8'));```

الكود يتوقع وجود **مجلد** اسمه `data` داخل الحاوية، والملفات موجودة بداخله. هذا التعارض في المسارات يتسبب في تعطل خادم Node.js فورًا عند محاولة تشغيله.

**الحل:**

نحتاج إلى تصحيح ملف `Dockerfile` ليقوم بنسخ مجلد `data` بأكمله بدلاً من نسخ الملفات بشكل فردي.

سأقوم بتعديل ملف `server/database/Dockerfile` لك.

هذا هو الكود المحدث والكامل للملف `server/database/Dockerfile`:

```dockerfile
FROM node:18.12.1-bullseye-slim

RUN npm install -g npm@9.1.3

WORKDIR /app

COPY package.json .
RUN npm install

COPY . .

EXPOSE 3030

CMD [ "node", "app.js" ]