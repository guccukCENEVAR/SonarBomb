
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
