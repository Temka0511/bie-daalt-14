# Эргэцүүлэл — REFLECTION.md

## 1. Хамгийн үнэ цэнэтэй assertion
Schema validation assertion хамгийн үнэ цэнэтэй санагдсан. 
Учир нь зөвхөн status code шалгах нь хангалтгүй — response-ийн 
бүтэц зөв байгааг баталгаажуулах нь API-ийн contract-ийг хамгаалдаг. 
Жишээ нь `id`, `email` property байгааг шалгасан нь API өөрчлөгдвөл 
шууд мэдэгдэх боломж олгоно.

## 2. Negative test
GET /users/999999 → 404 Not Found тест хамгийн чухал negative test байсан.
Энэ тест нь байхгүй resource-д хандахад API зөв алдаа буцаадаг эсэхийг 
шалгана. Хэрэв API 404 биш 200 буцаавал клиент код буруу ажиллах эрсдэлтэй.
Энэ тест нь "happy path" биш "error path"-ийг баталгаажуулдаг тул чухал.

## 3. Postman → Newman ялгаа
Postman-д амжилттай ажиллаж байсан тест Newman-д эхэндээ fail болсон.
Учир нь env.dev.json файлд baseUrl-ийн current value хадгалагдаагүй байсан.
Postman UI-д current value харагддаг ч export хийхэд initial value л хадгалагддаг.
Үүнийг файлыг гараар засаж шийдсэн.

## 4. Token болон secret зохицуулалт
JSONPlaceholder auth шаардахгүй тул token хэрэглээгүй. Гэхдээ 
env.dev.json-д baseUrl-г хадгалж, env.ci.json-д мөн адил бүтцийг ашигласан.
Secret байсан бол GitHub Secrets ашиглан CI-д environment variable болгон 
дамжуулах байсан. Real token-г хэзээ ч файлд шууд бичихгүй.

## 5. API өөрчлөгдвөл аль хэсэг эвдрэх вэ?
Schema validation тестүүд хамгийн эмзэг. Жишээ нь `email` field-ийн нэр 
`emailAddress` болвол бүх schema тест fail болно. Үүнийг бууруулахын тулд:
- Response-ийн заавал байх field-үүдийг л шалгах
- Нэмэлт field-үүдийг optional болгох
- API versioning ашиглах