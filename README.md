# iOS MOTION 26 (Android / One UI)

Samsung Galaxy A15 (One UI) için iOS 26 esintili Liquid Glass deneyimi. Kotlin + Android View sistemi, root gerekmez.

## APK nasıl indirilir (GitHub Actions)
1. Bu klasörü bir GitHub deposuna yükleyin (`main` dalı).
2. Depoda **Actions → Build APK** çalışır (ya da elle **Run workflow**).
3. APK iki yerde hazır olur:
   - **Releases → "iOS MOTION 26 - latest build"** → `iOS-MOTION-26.apk` (giriş gerektirmez)
   - **Actions → son çalışma → Artifacts → iOS-MOTION-26-apk**
4. Telefonda APK'yı açıp "bilinmeyen kaynaklardan yükle" iznini verin.

APK, depodaki `app/debug.keystore` ile imzalanır; güncellemeler eski sürümün üstüne kurulabilir.

## Gerçekten ne yapar / ne yapamaz
| Özellik | Durum |
|---|---|
| Liquid Glass (blur, kenar kırılması, yansıma, eğim sensörü) | Uygulama içinde gerçek. Blur için Android 12+ (A15'te var) |
| Denetim Merkezi (parlaklık, ses, fener, müzik, pil, döndürme) | Gerçek. Parlaklık/döndürme için "Sistem ayarlarını değiştir" izni |
| Wi-Fi / Bluetooth / Uçak modu | Android 10+ doğrudan açıp kapatmaya izin vermez → ilgili sistem paneli/ayarı açılır |
| Bildirim Merkezi | Gerçek; yalnızca siz bildirim erişimi verirseniz |
| Diğer uygulamaların üstünde kaydırma | Gerçek; sol üst tutamaç = Bildirimler, sağ üst tutamaç = Denetim Merkezi ("Diğer uygulamaların üzerinde göster" izni) |
| Sistem animasyon hızı | Yalnızca bir kerelik `adb shell pm grant com.iosmotion.app android.permission.WRITE_SECURE_SETTINGS` sonrası |
| Kilit ekranı | Uygulama içi arayüz; Samsung'un güvenli kilit ekranının yerine GEÇMEZ |
| One UI sistem animasyonlarını/launcher'ı değiştirme | Android izin vermez; yapılmaz |

Samsung notları: Ayarlar → Pil → "Uyuyan uygulamalar"dan iOS MOTION 26'yı çıkarın, aksi halde One UI arka plan servisini kapatabilir. One UI'nin kendi hızlı paneli üst kenardadır; tutamaçlar durum çubuğunun hemen altındadır.

## Test listesi (cihazda yapılmalı)
Etkinleştir/Devre dışı bırak, her anahtar, izin akışları, ayarların kalıcılığı (uygulamayı kapat/aç), ekran döndürme, geri hareketi, Denetim Merkezi kutucukları, bildirim kaydırma/temizleme, kilit ekranı (saat, hava, fener, kamera).
