# Planlama

Planlama, farklı bilgisayarlardan aynı GitHub reposu üzerinden geliştirilecek ortak bir proje çalışma alanıdır. Amaç; ev ve iş bilgisayarında Codex kullanırken aynı kod tabanı, dokümantasyon ve geliştirme kurallarıyla devam edebilmektir.

## Çalışma modeli

Projenin merkezi GitHub reposudur. Her bilgisayarda repository bir kez klonlanır; çalışmaya başlamadan önce son değişiklikler çekilir, yapılan değişiklikler commit edilip GitHub'a gönderilir.

```bash
git clone git@github.com:ekremkara22/Planlama.git
cd Planlama
```

Günlük çalışma başlangıcı:

```bash
git pull --rebase
```

Çalışma sonunda:

```bash
git status
git add .
git commit -m "Değişikliği kısa ve açıklayıcı biçimde yaz"
git push
```

## Codex ile çalışma

Codex her bilgisayarda repository kök dizininden çalıştırılmalıdır. Repository kökündeki `AGENTS.md`, Codex'in proje kurallarını ve çalışma biçimini tanımlar.

Codex ile yeni bir işe başlarken mümkün olduğunca net görevler verin. Örneğin:

```text
AGENTS.md kurallarına göre çalış.
Önce mevcut yapıyı incele.
Bu görev için gereken en küçük değişikliği yap.
Testleri çalıştır ve sonucu özetle.
```

## Repository yapısı

Başlangıçta temel yapı şöyledir:

```text
Planlama/
├── AGENTS.md
├── README.md
└── .gitignore
```

Uygulamanın teknoloji yığını belirlendiğinde kaynak kod, test, dokümantasyon ve yapılandırma klasörleri bu bölüme eklenecektir.

## Git çalışma kuralları

- `main` her zaman çalışır durumda tutulmalıdır.
- Büyük işler için ayrı branch kullanılması tercih edilir.
- Commit mesajları kısa, açıklayıcı ve tek bir değişikliği anlatacak şekilde yazılmalıdır.
- Secret, parola, API anahtarı, token ve kişisel ortam dosyaları Git'e eklenmemelidir.
- Bir bilgisayarda çalışmaya başlamadan önce `git pull --rebase` çalıştırılmalıdır.
- Aynı dosya iki bilgisayarda paralel değiştirilmemeye çalışılmalıdır.

Örnek branch akışı:

```bash
git switch -c feature/gorev-adi
# değişiklikleri yap
git add .
git commit -m "Görev açıklaması"
git push -u origin feature/gorev-adi
```

## Ortam dosyaları

Yerel ayarlar `.env` gibi Git'e gönderilmeyen dosyalarda tutulmalıdır. Gerektiğinde gerçek değer içermeyen bir `.env.example` dosyası repository içinde tutulabilir.

## Sonraki adımlar

Projenin amacı, kullanılacak teknoloji yığını, geliştirme komutları ve test stratejisi netleştikçe bu README güncellenecektir.
