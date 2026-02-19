<<<<<<< HEAD
# SonarBomb

[![Counter-Strike 2](https://img.shields.io/badge/CS2-Plugin-FF6B00?style=flat&logo=counter-strike)](https://store.steampowered.com/app/730/CounterStrike_2/)
[![CounterStrikeSharp](https://img.shields.io/badge/CounterStrikeSharp-1.0.362-00d4aa?style=flat)](https://github.com/roflmuffin/CounterStrikeSharp)
[![.NET 8](https://img.shields.io/badge/.NET-8.0-512BD4?style=flat&logo=dotnet)](https://dotnet.microsoft.com/)

**Saklambaç için Taktik Sonar Bombası** — Decoy (sahte bomba) grenadını, saklanan düşmanları tespit eden bir sonar cihazına dönüştüren Counter-Strike 2 eklentisi.

---

## İçindekiler

- [Genel Bakış](#genel-bakış)
- [Özellikler](#özellikler)
- [Gereksinimler](#gereksinimler)
- [Kurulum](#kurulum)
- [Komutlar](#komutlar)
- [Nasıl Çalışır](#nasıl-çalışır)
- [Derleme](#derleme)
- [Proje Yapısı](#proje-yapısı)
- [Yazar](#yazar)
- [Lisans](#lisans)

---

## Genel Bakış

SonarBomb, Saklambaç modları için tasarlanmış bir [CounterStrikeSharp](https://github.com/roflmuffin/CounterStrikeSharp) eklentisidir. Oyuncu bir "Sonar Bombası" (decoy) attığında, görüş hattındaki düşmanları tarar. Düşman tespit edilirse atan oyuncu bir ses uyarısı duyar.

## Özellikler

- **Sonar Tespiti** — Decoy atıldığında 3000 birim yarıçapta düşmanları tarar
- **Duvar Kontrolü** — [FUNPLAY Ray-Trace](https://github.com/FUNPLAY-pro-CS2/Ray-Trace) ile motor seviyesinde ışın izleme; yalnızca doğrudan görüş hattındaki düşmanları tespit eder
- **Market Kontrolü** — Aktifken alışveriş menüsünü kapatarak suiistimali engeller
- **Admin Komutları** — Sonar bombalarını belirli oyunculara veya takımlara dağıtın

## Gereksinimler

| Gereksinim | Bağlantı |
|------------|----------|
| Counter-Strike 2 + CounterStrikeSharp | [GitHub](https://github.com/roflmuffin/CounterStrikeSharp) |
| FUNPLAY Ray-Trace (Metamod) | [GitHub](https://github.com/FUNPLAY-pro-CS2/Ray-Trace) |
| .NET 8.0 | [İndir](https://dotnet.microsoft.com/download/dotnet/8.0) |

## Kurulum

1. En son sürümü indirin veya kaynaktan derleyin (bkz. [Derleme](#derleme))
2. `SonarBomb.dll` dosyasını `game/csgo/addons/counterstrikesharp/plugins` klasörüne koyun
3. [FUNPLAY Ray-Trace](https://github.com/FUNPLAY-pro-CS2/Ray-Trace) Metamod modülünü kurun ve yükleyin
4. Sunucuyu yeniden başlatın veya şu komutu çalıştırın: `css_plugins load SonarBomb`

## Komutlar

| Komut | Açıklama | Yetki |
|-------|----------|-------|
| `!sonarbomb` | Eklentiyi aç/kapat (marketi açar/kapatır) | `@css/generic` |
| `!sonar [hedef]` | Oyuncu(lar)a sonar bombası ver | `@css/generic` |
| `css_sonar [hedef]` | Konsol komutu — `!sonar` ile aynı | `@css/generic` |

### Hedef Parametreleri

| Hedef | Açıklama |
|-------|----------|
| `@me` | Kendine ver (varsayılan) |
| `@all` | Tüm canlı oyunculara ver |
| `@t` | Teröristlere ver |
| `@ct` | Anti-Teröristlere ver |
| `[isim]` | İsmi eşleşen oyuncuya ver (kısmi eşleşme) |

## Nasıl Çalışır

1. Admin `!sonarbomb` ile eklentiyi açar — market kapanır
2. Admin `!sonar @ct` (veya başka hedefler) ile sonar bombalarını dağıtır
3. Oyuncular decoy’ları "Sonar Bombası" olarak atar
4. Çarptığında eklenti, görüş hattında düşman var mı diye çok noktalı ışın izlemesi (kafa, göğüs, bel) yapar
5. 3000 birim içinde düşman tespit edilirse atan oyuncu bir bildirim sesi duyar
6. Decoy mermisi temiz bir efekt için kaldırılır

## Derleme

```bash
git clone https://github.com/KULLANICI_ADINIZ/SonarBomb-eng.git
cd SonarBomb-eng
dotnet build -c Release
```

Çıktı: `bin/Release/net8.0/SonarBomb.dll`

## Proje Yapısı

```
SonarBomb-eng/
├── SonarBomb.cs      # Ana eklenti mantığı
├── RayTrace.cs       # FUNPLAY Ray-Trace C# sarmalayıcı
├── SonarBomb.csproj  # Proje dosyası
├── README.md         # İngilizce
└── README.tr.md      # Türkçe
```

## Yazar

**guccukCENEVAR**

## Lisans

Depodaki [LICENSE](LICENSE) dosyasına bakın.
=======

🛰️ SonarBomb (CS2 Plugin)
SonarBomb, Counter-Strike 2 sunucuları için geliştirilmiş, özellikle "Saklanbaç" (Hide and Seek) modları için optimize edilmiş taktiksel bir admin ekipmanıdır. Decoy bombasını, fizik motoru seviyesinde tarama yapan sessiz bir sonar cihazına dönüştürür.

🌟 Özellikler
Akıllı Işın İzleme (Smart Trace): Aimbot.cs dosyasındaki mantığı kullanarak düşmanın sadece kafasına değil; göğüs ve bel bölgesine de ışın atar. Herhangi bir noktanın görünür olması sinyali tetikler.

Gelişmiş Duvar Filtreleme: RayTrace.cs wrapper'ı aracılığıyla sadece gerçek harita geometrisini (world, func_wall, static_prop) engel olarak görür. Diğer oyuncular veya şeffaf objeler taramayı engellemez.

Sessiz ve Gizli: Decoy yere düştüğü an sonar taramasını yapar ve anında yok edilir (projectile.AcceptInput("Kill")). Sahte silah sesleri çıkararak kafa karışıklığı yaratmaz.

Görsel Efekt (Beam Ring): Tarama yapıldığında, bombanın düştüğü noktada mavi bir şok dalgası (tagrenade_pulse) efekti oluşur.

Dinamik Market Kontrolü: Plugin aktif edildiğinde mp_buytime otomatik olarak 0 yapılır ve market kapatılır. Pasif edildiğinde market süresi (9999) tekrar açılır.

Özel Sesli Uyarı: Menzildeki düşmanlar tespit edildiğinde, bombayı atan adminin kulağına özel bir "Blink" sesi gelir.

⌨️ Komutlar
Komut	Yetki	Açıklama
!sonarbomb	Admin (@css/generic)	Plugini tamamen açar veya kapatır. Market kontrolünü yönetir.
!sonar <hedef>	Admin (@css/generic)	Belirlenen hedefe (@me, @all, @t, @ct) sonar bombası verir.
css_sonar <hedef>	Konsol / RCON	Konsol üzerinden sonar bombası verme komutu.
🛠️ Teknik Detaylar & Gereksinimler
Bu plugin, motor seviyesinde (engine-level) trace işlemleri gerçekleştirmek için FUNPLAY Ray-Trace Metamod modülüne ihtiyaç duyar.

Ray-Trace Modülü: CRayTraceInterface001 üzerinden signature scanning gerektirmeden çalışır.

İşlem Katmanları: Tarama sırasında MASK_SHOT_PHYSICS katmanı kullanılır.

👤 Geliştirici
guccukCENEVAR
>>>>>>> 4e0e606c6cbe897ee8b74233a0dd259821b66148
