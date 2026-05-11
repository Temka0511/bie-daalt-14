# Бие даалт 14 — API Testing

## API
JSONPlaceholder — https://jsonplaceholder.typicode.com

## Ажиллуулах заавар

### Newman суулгах
npm install -g newman newman-reporter-htmlextra

### Тест ажиллуулах
newman run postman/collection.json -e postman/env.dev.json

### HTML report үүсгэх
newman run postman/collection.json -e postman/env.dev.json --reporters cli,htmlextra --reporter-htmlextra-export reports/api.html