# AGENTS.md

Bu dosya, bu repository üzerinde çalışan Codex ajanları için kalıcı proje talimatlarını içerir.

## 1. Temel prensip

Önce repository'yi ve mevcut kodu incele, sonra değişiklik yap. Mevcut davranışı ve yapıyı anlamadan geniş kapsamlı refactor yapma.

Hedef her görevde mümkün olan en küçük, güvenli ve doğrulanabilir değişikliği üretmektir.

## 2. Göreve başlarken

Her görevde:

1. `git status` ile çalışma ağacını kontrol et.
2. İlgili dosyaları ve mevcut dokümantasyonu incele.
3. Kullanıcının isteğini mevcut mimariyle ilişkilendir.
4. Değişiklikten önce kısa bir uygulama planı oluştur.
5. Gereksiz dosyalara dokunma.

Kullanıcının mevcut değişikliklerini izinsiz silme, geri alma veya üzerine yazma.

## 3. Kod değişiklikleri

- Basit ve okunabilir çözümü tercih et.
- Gereksiz soyutlama oluşturma.
- Mevcut kod stilini koru.
- Aynı problemi çözen mevcut yardımcı fonksiyon veya bileşen varsa yeniden kullan.
- İlgisiz refactor yapma.
- Yeni bağımlılık eklemeden önce gerçekten gerekli olup olmadığını değerlendir.
- Secret, token, parola veya gerçek `.env` değerlerini kaynak koda yazma.

## 4. Dosya ve klasör yapısı

Yeni dosyaları mevcut mimariye uygun konuma ekle. Proje yapısı henüz oluşmamışsa teknoloji yığını belli olmadan gereksiz klasör ağacı oluşturma.

Repository kökündeki temel dokümanları güncel tut:

- `README.md`: insanlar için proje kurulumu ve kullanım bilgisi.
- `AGENTS.md`: Codex için kalıcı çalışma talimatları.
- `.gitignore`: yerel, geçici ve hassas dosyaların Git'e girmesini engeller.

## 5. Test ve doğrulama

Bir değişiklik yaptıktan sonra mümkün olan en ilgili doğrulamayı çalıştır.

Öncelik sırası:

1. Değiştirilen alanın hedefli testi.
2. İlgili test paketi.
3. Lint / type-check / build.
4. Gerekliyse daha geniş test paketi.

Test altyapısı yoksa bunu açıkça belirt. Test çalıştırmadan değişikliği doğrulanmış gibi sunma.

## 6. Git güvenliği

- Kullanıcı açıkça istemedikçe `git reset --hard`, zorla push veya geçmişi yeniden yazan tehlikeli işlemler yapma.
- Kullanıcının commit edilmemiş değişikliklerini koru.
- Başka bir bilgisayardan gelmiş değişiklikleri silme.
- Merge conflict oluşursa hangi tarafın korunacağı açık değilse tahmin ederek veri kaybettirme.
- Commit'leri mantıksal ve küçük tut.

## 7. Branch yaklaşımı

Küçük ve açık değişiklikler mevcut çalışma branch'inde yapılabilir. Daha büyük özellikler için açıklayıcı branch isimleri tercih et:

```text
feature/<kisa-aciklama>
fix/<kisa-aciklama>
refactor/<kisa-aciklama>
docs/<kisa-aciklama>
```

## 8. Commit mesajları

Kısa ve açıklayıcı mesajlar kullan. Tercihen Conventional Commits biçimini takip et:

```text
feat: add planning view
fix: handle empty task list
docs: update setup instructions
refactor: simplify date handling
test: add task creation tests
chore: update tooling
```

## 9. Dokümantasyon

Kurulum, çalışma komutları, environment değişkenleri veya mimari davranış değişirse ilgili dokümantasyonu da güncelle.

README'ye gerçek secret değerleri yazma. Environment değişkenleri gerekiyorsa yalnızca isimlerini ve amaçlarını belgeleyip örnek değerleri `.env.example` içinde tut.

## 10. Codex görev sonucu

Görev sonunda kısa şekilde şunları bildir:

- Ne değişti.
- Hangi önemli dosyalar değişti.
- Hangi test/doğrulamalar çalıştırıldı ve sonucu.
- Varsa bilinen risk veya sonraki adım.

Uzun ve gereksiz bir işlem günlüğü verme.

## 11. Çoklu bilgisayar çalışma düzeni

Bu repository ev ve iş bilgisayarından kullanılabilir. Bu nedenle yerel makineye özgü dosyaları repository'ye bağlama.

Kod ve gerekli proje yapılandırmaları Git üzerinden taşınmalıdır; cache, IDE durumu, credential ve kişisel ayarlar taşınmamalıdır.

Makineye özgü mutlak path kullanmaktan kaçın. Örneğin `C:\Users\...` veya `/Users/...` gibi yolları uygulama yapılandırmasına sabitleme.

## 12. Talimat önceliği

Kullanıcının o anki açık talimatı bu dosyadaki genel tercihlerden daha önceliklidir. Ancak veri kaybı, secret sızıntısı veya geri döndürülmesi zor Git işlemleri konusunda dikkatli davran.

Alt klasörlerde daha spesifik bir `AGENTS.md` bulunursa, o klasördeki işler için daha spesifik talimatları uygula.
