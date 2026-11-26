# Krallık Seferi — örnek v0.8

Mount & Blade: Warband'in oynanışını 2D kuşbakışı çizimle mobile taşıyan oyunun oynanabilir örneği. Tek dosya HTML5 (WebGL2 + Canvas 2D), yatay ekran.

## Dosyalar
- `index.html` — oyunun tamamı. Tarayıcıda açınca çalışır.
- `app/`, `build.gradle`, `settings.gradle`, `gradle.properties` — Android WebView projesi (yatay kilit, tam ekran, reklamsız).
- `.github/workflows/apk.yml` — GitHub Actions ile APK derlemesi.

## APK nasıl çıkar
1. GitHub'da boş bir depo aç (örnek: `krallik-seferi`).
2. Bu klasördeki her şeyi (gizli `.github` klasörü dahil) deponun `main` dalına yükle.
3. Actions sekmesinde "APK uret" kendiliğinden çalışır (elle de başlatılabilir).
4. Bitince çalışmanın altındaki `krallik-seferi-apk` dosyasını indir, içindeki `.apk`'yı telefona kur. Telefonda "bilinmeyen kaynaklardan yükleme" izni gerekebilir.

Oyunu güncellemek için yalnız `index.html` dosyasını değiştirip yüklemek yeter; Actions yeni APK'yı üretir.

Not: APK test için debug anahtarıyla imzalı. Play Store için ayrı bir imza anahtarı gerekir.

## Oyunda olanlar
- **Başlangıç:** 5 millet (Arvelin Krallığı, Gökbörü Hanlığı, Zerran Sultanlığı, Varhelm Jarllığı, Serenza Cumhuriyeti).
- **Dünya haritası:** 16800×10500 birim, karo (parça) sistemiyle çizilir; uzaktan genel görünüm. İç denizli coğrafya: ortada büyük deniz, boğazla bağlı kuzey denizi, doğuda büyük göl, güneyde körfezler ve adalar; güneyde çöl kuşağı. Yol çizgisi yok. Yer adları krallık renginde. Her millette 1 başkent, ~5 şehir, ~4 kale, ~17 köy (toplam ~130 yerleşim), 30 lord ordusu, 60 haydut çetesi. Zaman yalnız yürürken ya da "Bekle" ile akar; gece/gündüz.
- **Ordu döngüsü:** 500 altın, 30 yemek, 75 moral, 10 nam ile başlar. Kapasite 20 + nam/5. Her gün yemek (asker/5); yeterse moral +1.5, yetmezse −10; moral < 20 ise asker kaçar. Haftalık maaş. Yaralılar zamanla iyileşir.
- **Şehir/köy:** pazar, meyhane (paralı asker), han, gönüllü toplama, köy pazarı, tarlada çalışma.
- **Ordu ekranı:** 33 asker türü (millet başına 6 + 3 haydut), XP ve dallanan terfi ağacı.
- **Savaş öncesi hazırlık:** 4 savaş planı (Hat savunması, Kanat kuşatması, Topyekûn hücum, Okla yıprat), birlik başına diziliş (Saf/Derin/Gevşek) ve başlangıç emri, kendi alanına yerleştirme, 4 yetenekten 2'si (Ok yağmuru, Mızrak duvarı, Kanat hücumu, Savaş narası).
- **Savaş:** kahramanı sen yönetirsin (sol: joystick, sağ: dokun = kalkan, basılı tut-bırak = saldırı, yukarı kaydır = dürt). Emirler sınıfa göre: Beni takip et, Hücum, Pozisyonu koru, Kalkan duvarı; emir açıkken zaman 0.25×. En fazla 300 asker. Hasar: hız bonusu, önden kalkan %75, zırh.
- **Sonuç:** ganimet, nam, XP; ölenlerin yarısı ölü, yarısı yaralı.
- **Kayıt:** her gün başında ve uygulama kapanırken otomatik.

## Klavye (bilgisayarda)
WASD yürü · Boşluk basılı tut-bırak saldırı (Shift = dürt) · sağ tık kalkan · Q emir · R çekil.

## Performans
300 askerlik savaş, 4× CPU yavaşlatmada 60 FPS. Otomatik kalite: FPS 50'nin altına düşerse çözünürlük kademeli düşer.

## Sıradaki adımlar
- Şehir içi yerleşimi düzenlemek, uzak haritada dağ/kar lekelerini temizlemek.
- Millet başına ~9 asker türü, kahraman özellikleri ve ekipman, kuşatma, diplomasi, turnuva.
