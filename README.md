# กระปุก (แอปออมเงินออฟไลน์)

แอปตั้งเป้าหมายออมเงิน ฝาก/ถอน ดูประวัติ ใช้ได้โดยไม่ต้องมีอินเทอร์เน็ต
ข้อมูลเก็บในเครื่องเท่านั้น มีปุ่มสำรอง/กู้คืนข้อมูลในหน้าตั้งค่า

## ได้ไฟล์ APK แบบไหนง่ายที่สุด (ไม่ต้องลง Android Studio)

1. สมัคร GitHub (ฟรี) แล้วสร้าง repository ใหม่
2. อัปโหลดไฟล์ทั้งหมดในโฟลเดอร์นี้ขึ้นไป (รวมโฟลเดอร์ `.github`)
3. เปิดแท็บ **Actions** แล้วรอ workflow ชื่อ **Build APK** รันเสร็จ (ราว 5-8 นาที)
   ถ้าไม่รันเอง ให้กด **Run workflow**
4. เปิดงานที่รันเสร็จ ดาวน์โหลดไฟล์ `krapuk-apk` ตรงหัวข้อ Artifacts แล้วแตกซิป จะได้ `app-debug.apk`
5. ส่งไฟล์เข้ามือถือ เปิดติดตั้ง (อาจต้องอนุญาต "ติดตั้งแอปจากแหล่งที่ไม่รู้จัก")

## สร้างเองในเครื่อง

ต้องมี Node.js 18+, JDK 17 และ Android Studio (หรือ Android SDK)

```
npm install
npx cap add android
npm run icons
npx cap sync android
cd android && ./gradlew assembleDebug
```

ไฟล์ที่ได้อยู่ที่ `android/app/build/outputs/apk/debug/app-debug.apk`

## หมายเหตุ

- APK ที่ได้เป็นแบบ debug ใช้ติดตั้งเองได้เลย ถ้าจะขึ้น Play Store ต้องทำ release build และเซ็นกุญแจก่อน
- แก้หน้าตาแอปที่ `www/` (index.html, style.css, app.js) แล้วสร้าง APK ใหม่
- เปลี่ยนไอคอนโดยแทนที่ `resources/icon.png` (1024x1024)
- ถ้าถอนการติดตั้งแอป ข้อมูลจะหาย ควรกดสำรองข้อมูลไว้ก่อน
