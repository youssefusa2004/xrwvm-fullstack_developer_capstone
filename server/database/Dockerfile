FROM node:18.12.1-bullseye-slim

WORKDIR /app

# نسخ package.json و package-lock.json (إن وجد)
COPY package*.json ./

# تثبيت الاعتماديات أولاً للاستفادة من التخزين المؤقت
RUN npm install

# نسخ بقية ملفات التطبيق
COPY . .

EXPOSE 3030

CMD [ "node", "app.js" ]